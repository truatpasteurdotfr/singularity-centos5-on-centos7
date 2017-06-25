# CentOS-5 singularity container bootstrap from a CentOS-7 host
- you need to install compat-db43 from either CentOS-6 or rebuild compat-db-4.6.21-17.el6.src.rpm on CentOS-7
- compat-db-4.6.21-17.el6.src.rpm and compat-db43-4.3.29-15.el6.x86_64.rpm pulled from CentOS-6
- replacing the original CentOS-Base.repo with one pointing to the archived vault.centos.org

# CentOS-5 has been End of Life (no support/no bug fix/...) since 31 March 2017.
(https://lists.centos.org/pipermail/centos-announce/2017-April/022350.html)

# howto:
1) Install compat-db43 
```
yum install compat-db43-4.3.29-15.el6.x86_64.rpm
```
or using https://wiki.centos.org/HowTos/SetupRpmBuildEnvironment to prepare your rpmbuild environment:
```
rpmbuild --rebuild compat-db-4.6.21-17.el6.src.rpm && sudo yum install ~/rpmbuild/RPMS/x86_64/compat-db43-4.3.29-17.el7.centos.x86_64.rpm
```
2) singularity
```
singularity create c5-on-c7.img
sudo singularity bootstrap c5-on-c7.img singularity-centos5-on-centos7.def
```

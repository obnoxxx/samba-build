# Samba CentOS/Fedora RPM Builds

[![status](<https://jenkins-samba.apps.ocp.cloud.ci.centos.org/buildStatus/icon?job=samba_build-rpms-fedora39-master&subject=master / Fedora 39>)](https://jenkins-samba.apps.ocp.cloud.ci.centos.org/job/samba_build-rpms-fedora39-master/) [![status](<https://jenkins-samba.apps.ocp.cloud.ci.centos.org/buildStatus/icon?job=samba_build-rpms-fedora39-v4-19-test&subject=v4-19-test / Fedora 39>)](https://jenkins-samba.apps.ocp.cloud.ci.centos.org/job/samba_build-rpms-fedora39-v4-19-test/) [![status](<https://jenkins-samba.apps.ocp.cloud.ci.centos.org/buildStatus/icon?job=samba_build-rpms-fedora39-v4-20-test&subject=v4-20-test / Fedora 39>)](https://jenkins-samba.apps.ocp.cloud.ci.centos.org/job/samba_build-rpms-fedora39-v4-20-test/)

[![status](<https://jenkins-samba.apps.ocp.cloud.ci.centos.org/buildStatus/icon?job=samba_build-rpms-fedora40-master&subject=master / Fedora 40>)](https://jenkins-samba.apps.ocp.cloud.ci.centos.org/job/samba_build-rpms-fedora40-master/) [![status](<https://jenkins-samba.apps.ocp.cloud.ci.centos.org/buildStatus/icon?job=samba_build-rpms-fedora40-v4-19-test&subject=v4-19-test / Fedora 40>)](https://jenkins-samba.apps.ocp.cloud.ci.centos.org/job/samba_build-rpms-fedora40-v4-19-test/) [![status](<https://jenkins-samba.apps.ocp.cloud.ci.centos.org/buildStatus/icon?job=samba_build-rpms-fedora40-v4-20-test&subject=v4-20-test / Fedora 40>)](https://jenkins-samba.apps.ocp.cloud.ci.centos.org/job/samba_build-rpms-fedora40-v4-20-test/)

[![status](<https://jenkins-samba.apps.ocp.cloud.ci.centos.org/buildStatus/icon?job=samba_build-rpms-centos8-master&subject=master / CentOS 8>)](https://jenkins-samba.apps.ocp.cloud.ci.centos.org/job/samba_build-rpms-centos8-master/) [![status](<https://jenkins-samba.apps.ocp.cloud.ci.centos.org/buildStatus/icon?job=samba_build-rpms-centos8-v4-19-test&subject=v4-19-test / CentOS 8>)](https://jenkins-samba.apps.ocp.cloud.ci.centos.org/job/samba_build-rpms-centos8-v4-19-test/) [![status](<https://jenkins-samba.apps.ocp.cloud.ci.centos.org/buildStatus/icon?job=samba_build-rpms-centos8-v4-20-test&subject=v4-20-test / CentOS 8>)](https://jenkins-samba.apps.ocp.cloud.ci.centos.org/job/samba_build-rpms-centos8-v4-20-test/)

[![status](<https://jenkins-samba.apps.ocp.cloud.ci.centos.org/buildStatus/icon?job=samba_build-rpms-centos9-master&subject=master / CentOS 9>)](https://jenkins-samba.apps.ocp.cloud.ci.centos.org/job/samba_build-rpms-centos9-master/) [![status](<https://jenkins-samba.apps.ocp.cloud.ci.centos.org/buildStatus/icon?job=samba_build-rpms-centos9-v4-19-test&subject=v4-19-test / CentOS 9>)](https://jenkins-samba.apps.ocp.cloud.ci.centos.org/job/samba_build-rpms-centos9-v4-19-test/) [![status](<https://jenkins-samba.apps.ocp.cloud.ci.centos.org/buildStatus/icon?job=samba_build-rpms-centos9-v4-20-test&subject=v4-20-test / CentOS 9>)](https://jenkins-samba.apps.ocp.cloud.ci.centos.org/job/samba_build-rpms-centos9-v4-20-test/)

This repository contains automation to create [Samba](https://www.samba.org/) RPMs for CentOS Stream 8/9 and
Fedora from the upstream  [code repository](https://git.samba.org/samba.git). In order to allow building from a variety of git
refspecs, the following make target format is used:

`$ make < rpms.centos8 | rpms.centos9 | rpms.fedora > [ vers=< fedora-version > refspec=< branch-name | tag-name | h:<git-commit-hash> > ]`

A Few examples:

```console
$ make rpms.centos8 refspec=v4-20-test
$ make rpms.centos9 refspec=h:a0862d6d6de
$ make rpms.fedora vers=39 refspec=samba-4.19.6
```

As of now, versions  4.19 and  4.20 and the master branch are supported. In the absence of the 
*refspec* argument, the master branch is built by default. The above format is
also applicable for other `make` targets. The *vers* argument is only valid for
Fedora related make targets and specifies the Fedora version to build for. In its absence, the default version is
set to *40*.

Except on CentOS Stream 8, in addition to vfs-glusterfs and vfs-cephfs, Active
Directory Domain Controller components are also built as RPMs.

These are automatically run as nightly jobs for CentOS Stream 8/9 and
Fedora 39/40 on [centos-ci](https://jenkins-samba.apps.ocp.cloud.ci.centos.org/view/RPM)
and published as [yum repositories](https://artifacts.ci.centos.org/samba/pkgs/).

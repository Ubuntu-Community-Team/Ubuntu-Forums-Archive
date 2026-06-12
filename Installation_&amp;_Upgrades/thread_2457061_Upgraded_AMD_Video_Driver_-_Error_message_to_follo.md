---
title: "Upgraded AMD Video Driver - Error message to follow"
date: 2021-01-25
forum: Installation &amp; Upgrades
---

### Post by backspin on 2021-01-25
Last night I tried to upgrade my AMD video driver for my 5700XT Card.  Any ideas on the best way of fixing this issue?

Upgrading from -  amdgpu-pro-20.40-1147286-ubuntu-20.04
Upgrading To -     amdgpu-pro-20.45-1188099-ubuntu-20.04

$./amdgpu-install -y --opencl=pal

Putting in the Errors -- 

ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/amdgpu-dkms-firmware.0.crash'
Error! Bad return status for module build on kernel: 5.8.0-40-generic (x86_64)
Consult /var/lib/dkms/amdgpu/5.6.20.906316-1188099/build/make.log for more information.
dpkg: error processing package amdgpu-dkms (--configure):
 installed amdgpu-dkms package post-installation script subprocess returned error exit status 10
dpkg: dependency problems prevent configuration of amdgpu:
 amdgpu depends on amdgpu-dkms (= 1:5.6.20.906316-1188099); however:
  Package amdgpu-dkms is not configured yet.

dpkg: error processing package amdgpu (--configure):
 dependency problems - leaving unconfigured
Setting up xserver-xorg-amdgpu-video-amdgpu (1:19.1.0-1188099) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Sett
ing up mesa-amdgpu-omx-drivers:amd64 (1:20.1.6-1188099) ...

dpkg: dependency problems prevent configuration of amdgpu-pro-rocr-opencl:
 amdgpu-pro-rocr-opencl depends on amdgpu-dkms (= 1:5.6.20.906316-1188099); however:
  Package amdgpu-dkms is not configured yet.

dpkg: error processing package amdgpu-pro-rocr-opencl (--configure):
 dependency problems - leaving unconfigured
Setting up libosmesa6-amdgpu:amd64 (1:20.1.6-1188099) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Sett
ing up libosmesa6-amdgpu:i386 (1:20.1.6-1188099) ...


Errors were encountered while processing:
 amdgpu-dkms
 amdgpu
 amdgpu-pro-rocr-opencl
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ActionParsnip on 2021-01-25
Rename /var/crash/amdgpu-dkms-firmware.0.crash and retry

---

### Post by backspin on 2021-01-25
renamed and uninstalled driver and then re-installed.

Unfortunately, same issue :(

---


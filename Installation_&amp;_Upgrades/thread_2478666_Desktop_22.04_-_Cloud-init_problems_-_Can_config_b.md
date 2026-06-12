---
title: "Desktop 22.04 - Cloud-init problems - Can config be served over ftp instead of http?"
date: 2022-09-01
forum: Installation &amp; Upgrades
---

### Post by gutyex on 2022-09-01
I have set up an iPXE based toolset for a computer repair shop with various bootable tools including Ubuntu 22.04 desktop ISO.  

I would like to include the option of an automated install by serving a cloud-init config from the NAS which is currently serving the various boot images via FTP. All examples I have seen of starting autoinstall via PXE have the config files served via HTTP, but would simplify things for me if I could avoid setting up an HTTP server on top of everything else.  
  
I have tried the following iPXE config which successfully boots to the live desktop environment but does not start the autoinstall process, all I can see in the syslog is it picking up the imgargs values but no errors to suggest why it isn't attempting to autoinstall.

```

kernel ftp://freenas/vmlinuz
initrd ftp://freenas/initrd
imgargs vmlinuz initrd=initrd autoinstall url=ftp://freenas/ubuntu.iso ip=dhcp ds=nocloud-net;s=ftp://freenas/Ubuntu/

```

[ftp://freenas/Ubuntu/](ftp://freenas/Ubuntu/) is a folder containing user-data and meta-data files

---


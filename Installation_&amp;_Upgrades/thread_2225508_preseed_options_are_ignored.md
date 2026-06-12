---
title: "preseed options are ignored"
date: 2014-05-21
forum: Installation &amp; Upgrades
---

### Post by nixgeek on 2014-05-21
Hey all,

I have a ipxe boot setup and a local ubuntu mirror [trusty]
All is well, except preseeding issues, the goal is to make it more automated.

When I use the following for the mirror section:

d-i mirror/country string manual
d-i mirror/http/hostname string 192.168.0.33
d-i mirror/http/directory string /ubuntu/
d-i mirror/http/proxy string
d-i mirror/http/mirror select 192.168.0.33


I am still prompted to select a mirror from a list of countries.   Any ideas why it is ignoring this?
I can manually add this above in the "enter information manually" option and it begins the install
just fine.

here is my ipxe bootstrap ubuntu section:

:ubuntu
echo Starting Ubuntu install ${archl}
set base-url [http://192.168.0.33/ubuntuinstall/14.04/amd64/install/netboot/ubuntu-installer/amd64](http://192.168.0.33/ubuntuinstall/14.04/amd64/install/netboot/ubuntu-installer/amd64)
kernel ${base-url}/linux
initrd ${base-url}/initrd.gz
imgargs linux auto=true fb=false url= [http://192.168.0.33/ubuntu-server.seed](http://192.168.0.33/ubuntu-server.seed)
boot || goto failed
goto start
 

So it is reading the pre-seed file but seems to ignore some options.
The above kernel and initrd is from the Server CD, /install/netboot/ubuntu-installer/amd64

I am using a VM in Vmware esxi host 5.5.

Like I said I can manually enter the host and directory and it installs without issue. I am
looking to make this more automated.

Any advice is welcome.

Yes I did many hours of research on this.

Tim

---


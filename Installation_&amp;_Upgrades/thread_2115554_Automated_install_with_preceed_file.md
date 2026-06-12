---
title: "Automated install with preceed file"
date: 2013-02-13
forum: Installation &amp; Upgrades
---

### Post by kbensch on 2013-02-13
Good day

I have been working with Centos for some time and have created many automated installs. Its really easy. All that is required to start an automated installation on centos without the need for dhcp, dns, tftp, pxelinux and any other components I left out, is a kickstart file, a location to put the kickstart file and then the minimal boot image.

I can then type the following at the boot: prompt:

linux ks=http://where/my/ks/file/is.cfg ksdevice=eth0

I recently started a new position and they use ubuntu.

Having read manuals and posts for the last 2 days, it seems that I have to setup a dns/dhcp server with tftp and pxe to get an automated install from a preseed file to work. Is there a way I can type a similar command like this:

linux ks=http://where/my/ks/file/is.cfg ksdevice=eth0

on ubuntu to install it using the preseed file?

I hear your question, why dont i set up the pxe environment?

Cause I am busy with R&D and dont want to set that up in my test env just yet.

Any help would be appreciated.

Kobus

---

### Post by schragge on 2013-02-13
See [here]("http://www.debian.org/releases/stable/amd64/apbs02.html.en#preseed-loading").

---

### Post by kbensch on 2013-02-13
Thank you for the reply. I have actually already read this and maybe there is something I dont understand or soemthing I am missing completely.

I have tried to boot woth the preseed by pressing f6 and then adding 
preseed/url=http://host/path/to/preseed.cfg after the --

This does not work. It just boots and then asks all of the questions which is in the preseed. I have also tried to run 

install preseed/url=http://host/path/to/preseed.cfg

Same thing. It continues the installation by asking all of the questions I have put in the preseed.

When Centos starts the installation, I can see it assigning the IP address for the net install as it also uses network available repositories. At which stage does ubuntu enable the network? maybe I am missing something on the network setup before the preseed loads.

Kobus

---

### Post by schragge on 2013-02-13
> **kbensch said:**
> then adding 
preseed/url=http://host/path/to/preseed.cfg after the --

This does not work. It just boots and then asks all of the questions which is in the preseed. I have also tried to run 

install preseed/url=http://host/path/to/preseed.cfgThat's wrong. The kernel boot parameters should be something like
```

auto url=http://host/path/to/preseed.cfg

```
Look it up a little further down on the page I linked.

---


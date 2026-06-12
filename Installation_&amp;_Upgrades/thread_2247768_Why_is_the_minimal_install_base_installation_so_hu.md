---
title: "Why is the minimal install base installation so huge (1.73GB?)"
date: 2014-10-10
forum: Installation &amp; Upgrades
---

### Post by shai-shaibn on 2014-10-10
Hello,

I'm trying to create a Vagrant box that is based on Ubuntu 14.04 LTS. I'm doing this by installing Ubuntu on a fresh Virtualbox VM.
I downloaded the mini.iso and ran the installation (pretty basic) and it automatically started the "Installating the base system" part ... by the end of it, the virtual hard disk was 1.73GB!

Can someone help me understand how I can get about installing the really bare, basic, minimal installation that won't be more then 300-500MB?
Just for comparison, I've seen Vagrant boxes on Vagrantbox (.) es ; that are 362MB for the amd64 architecture.

---

### Post by slickymaster on 2014-10-10
Hi shai-shaibn, welcome to the forums.

A minimal installation of trusty requires 400MB of disk space. The standard Ubuntu desktop installation requires 2GB.

Please refer to:
[LIST]
[*][https://help.ubuntu.com/14.04/installation-guide/powerpc/ch03s04.html#idp5424720](https://help.ubuntu.com/14.04/installation-guide/powerpc/ch03s04.html#idp5424720)
[*][https://help.ubuntu.com/14.04/installation-guide/powerpc/apds03.html](https://help.ubuntu.com/14.04/installation-guide/powerpc/apds03.html)
[/LIST]

---

### Post by shai-shaibn on 2014-10-10
Thank you for the warm welcome :)

Ok, I read the links and tried it again (because I've already tried it before) just to make sure I've not missed out on anything ... so I got the Ubuntu Server ISO ([http://releases.ubuntu.com/trusty/ubuntu-14.04.1-server-amd64.iso](http://releases.ubuntu.com/trusty/ubuntu-14.04.1-server-amd64.iso)) and so I decided to record the installation AND show the virtual hard disk grow as the installation begins. The video is approx. 4:30min but you start seeing the increase @ around 1:20min.

[https://www.youtube.com/watch?v=aSoBen6sm34#t=86](https://www.youtube.com/watch?v=aSoBen6sm34#t=86)

Please, help me figure this out .. I must be doing something wrong as the help does show that a 400MB is the minimum .. and that's what I want to achieve.

Thanks in advance!

---

### Post by sudodus on 2014-10-10
The ***9w*** installer can install Trusty 32-bit systems of various size and complexity. The minimum system (still complete with a portable wired network) uses 34 MB RAM when running idle, and occupies 1.1 GiB disk space. These systems were ***originally made from the Ubuntu mini.iso***.

[TABLE]
[TR]
[TD="bgcolor: #CCFF99, colspan: 4"]Installed system developed from Ubuntu 14.04 LTS mini.iso
[/TD]
 [/TR]
 [TR]
  [TD="bgcolor: #DDFFAA"]Description
[/TD]
   [TD="bgcolor: #DDFFAA"]RAM 
[/TD]
   [TD="bgcolor: #DDFFAA"]Disk
[/TD]
   [TD="bgcolor: #DDFFAA"]Comments

[/TD]
 [/TR]
 [TR]
  [TD="bgcolor: #CCFF99"]
[/TD]
   [TD="bgcolor: #CCFF99"]MiB
[/TD]
   [TD="bgcolor: #CCFF99"]GiB
[/TD]
   [TD="bgcolor: #CCFF99"][/TD]
 [/TR]
 [TR]
  [TD]Ubuntu minimal text 
[/TD]
   [TD]034
[/TD]
   [TD]1.1
[/TD]
   [TD] 

[/TD]
 [/TR]
 [TR]
  [TD]Fluxbox, xinit, xterm
[/TD]
   [TD]058
[/TD]
   [TD]1.3
[/TD]
   [TD]no effort for sound
[/TD]
 [/TR]
 [TR]
  [TD]Openbox in LXDE
[/TD]
   [TD]062
[/TD]
   [TD="colspan: 2, align: center"][/TD]
 [/TR]
 [TR]
  [TD]LXDE
[/TD]
   [TD]074
[/TD]
   [TD]1.6
[/TD]
   [TD]no sound in speakers
[/TD]
 [/TR]
 [TR]
  [TD]Lubuntu Core, midori, leafpad
[/TD]
   [TD]125
[/TD]
   [TD]2.3
[/TD]
   [TD]lubuntu restricted extras
[/TD]
 [/TR]
 [TR]
  [TD]Lubuntu desktop
[/TD]
   [TD]123
[/TD]
   [TD]2.8
[/TD]
   [TD]lubuntu restricted extras
[/TD]
 [/TR]
 [TR]
  [TD]Xubuntu desktop
[/TD]
   [TD]246
[/TD]
   [TD]3.1
[/TD]
   [TD]xubuntu restricted extras
[/TD]
[/TR]
[/TABLE]

See this link (and the web page above it) for more details

[https://help.ubuntu.com/community/9w/RAM_%26_disk_usage](https://help.ubuntu.com/community/9w/RAM_%26_disk_usage)

-o-

If you want really small systems,  I suggest you start from another linux distro, for example Debian, Tiny Core, Puppy, DSL.

---

### Post by shai-shaibn on 2014-10-10
Does that mean that the aforementioned help documentation that specifies that it can have a minimum of 400MB used on the disk is no relevant / up-to-date?

---

### Post by sudodus on 2014-10-10
If we are talking about an ***installed system***, I think you might be able to have such a system with only 400 MB, but I don't think it would be very useful, if based on Ubuntu. (My attempt landed at 1.1 GB.)

-o-

If we are talking about a ***live system*** (using a compressed archive, squashfs) which will be expanded and running in RAM, the stored system (as an ISO file or as installed in a CD drive), it can be 400 MB and still working.

The standard Lubuntu desktop ISO files are still within CD size ~700 MB.

***Edit***: Tiny Core comes as a working desktop ISO file. It is only 14 GiB (14680064 bytes)

```
-rw-rw-r-- 1 sudodus sudodus [COLOR=#0000ff]14680064[/COLOR] okt  1 10:03 TinyCore-5.4.iso
```

---

### Post by shai-shaibn on 2014-10-10
Agreed. 1.1GB to 1.8GB is what one should expect out of this minimal installation.

---


---
title: "Reporting different versions"
date: 2012-10-31
forum: Installation &amp; Upgrades
---

### Post by wandiligong on 2012-10-31
Hi Forum

I have been running Ubuntu 10.10 satisfactorily on an older PC
Decided to upgrade to 11.04
This went OK but some inconsistency with playing music with Rythmbox and network connection.
I notice that System Monitor reports PC is running Release 10.10 but "About Ubuntu"says "You are using 11.04"
Why does system tell me I am running two different versions?

I thought I might solve inconsistency of operation by installing 12.10 but don't know if I can upgrade (as system reports two releases) so I downloaded 12.10 thinking to run off the DVD.
My system recognises the DVD to boot from but I only get a screen with Ubuntu 12.10 on it but it never starts. If I press F6 at the start of the boot I can get the choice screen (Run from disc, install check memory, etc) 
This screen gives some options (acpi=off, no apic, etc) but I can't edit the boot line to replace "splash" comment as I have read in install instructions. 
I could just do a new install of 12.10 but am wary if it does not run from DVD

Any suggestions would be welcome

---

### Post by 2F4U on 2012-10-31
First of all, 11.04 is EOL, so it is probably not a good idea to stay with that release.
 
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Secondly, if I were you, I would try 12.04 instead of 12.10, because 12.10 seems to have some issues at the moment. Thirdly, if you have problems to boot 12.10, please post your hardware specifications.

To edit the grub2 line, read through this:

[https://help.ubuntu.com/community/Grub2/Troubleshooting#Editing_the_GRUB_2_Menu_During_Boot](https://help.ubuntu.com/community/Grub2/Troubleshooting#Editing_the_GRUB_2_Menu_During_Boot)

---

### Post by wandiligong on 2012-11-02
Thanks 2F4U
 
I downloaded 12.04.1 and am now running from DVD OK.
 
Sound problems now disappeared.
 
I am trying to sort out network connection. My recollection with 12.10 I had to have network recognized as a server and supply password. Dont seem to be able to see the same thing in 12.04 but will explore a little more
 
If I do a new install with 12.04 will I retain my data?

---

### Post by grahammechanical on 2012-11-02
> f I do a new install with 12.04 will I retain my data?

Only if you have /home on a separate partition and you mount that partition as /home but do **not** partition it. If you only have a home folder in the / partition then a fresh install with formatting will wipe out your data.

It is possible to install over an existing Ubuntu and not mark the partition to be formatted. This may or may not keep your home folder with its data and settings safe. That may be fine when re-installing the same version of Ubuntu. I have done this in the past after backing up my valuable data.

You are going from one version to another. You will end up with obsolete libraries from 10.10/11.04 (whatever, it is called) still in the partition.

12.04 has completely new libraries even over 11.04.

Regards.

---

### Post by wandiligong on 2012-11-03
Thanks Grahammechanical

I have done an upgrade (after backing up data) system said it could not install some functions and I might have to install manually but it seems to work OK System shows release 12.04 LTS

Sound OK, network printer OK

Now I just have to work thru networking with other PC

Thanks for your comments

---


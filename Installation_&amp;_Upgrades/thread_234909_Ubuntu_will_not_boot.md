---
title: "Ubuntu will not boot"
date: 2006-08-12
forum: Installation &amp; Upgrades
---

### Post by InDenial on 2006-08-12
Hi all,

I installed Ubuntu 6.06 TLS (server) on a Pentium 200 MMX. it has 128 M of ram. This worked well with Ubuntu breezy. My harddisk crashed a week ago and I decided to buy a bigger harddisk (120 Gig) It came in today, put it in and started installing Ubuntu. Installation went fine.. no problems there.

When the computer boots I see it starting grub, and after it says boot it just restarts the comp. it never gives me any errors either.

It might be that the disk is to big for the comp (compaq deskpro).

The weird thing is that when I go in and configure the bios it says it's a 120 Gig HD. But when I disconnect the harddisk , reboot the comp, then reconnect it again and reboot again it shows a message saying:

> The following configuration options were automaticly updated: Disk 1:**54498** Mbytes
If you are using Unix you need to configure your system using the COMPAQ User Diagnostics diskette

I did not try that yet btw. Because if I can install Linux on it this should not be the problem. (It ran very good with a 40 Gig HD)

Did anything like this ever happen to someone else?.. I could not find any information on this online. I would like some help of a link to a site which describes this problem. (I might have looked in the wrong places)

Thanks in advance for taking the time.... :-)

---

### Post by ubunzu on 2006-08-12
I would say at a guess that the BIOS is not detecting your 120GB drive properly as it seems to think you have 53GB drive installed. Try to see if you can get a BIOS update which may have support for larger drives. Out of curiousity have you successfully booted the machine using the live CD (apart from at install time)?

---

### Post by InDenial on 2006-08-12
Hi,

I tried to use the live cd and this booted correctly (although I had to use safe graphics mode. probably crappy graphics card) It booted up fine.

Then I thought well lets install the compaq bios stuff onto the harddisk and see what happens. I did that and installed ubuntu again (again flawless) and rebooted to start it for the first time and again it keeps rebooting.

here is something interesting:

When I started the install again to just remove the partitions because I needed the space to put the compaq partition I saw that all the partitions were pointing to /media/hdax and not to root, boot or home. 

I am going to use an old version like breezy to see if it is the harddisk or an ubuntu bug..

---

### Post by confused57 on 2006-08-12
There's a problem with the Dapper server iso with older computers, just continually reboots the system after installing.  You can install a server using the Dapper alternate cd.
I tried several different downloaded Dapper server iso's burned to cd, but they all just caused my AMD K6-2 500mhz to continually reboot.  I had no problem installing to a Dell Dimension 4550, 2.0 GHz.

---

### Post by InDenial on 2006-08-12
Thanks I will try it .. I installed UBuntu breezy and it worked. I will try to use the alternate cd. will post back when I am done.

---

### Post by InDenial on 2006-08-12
Thanks confused57 it worked... :-)

---

### Post by jameshartford on 2006-08-19
I am having the same problem on a compaq presario 7360.  I was able to finally boot from cd using the server version of ubuntu, and the install when fine, but now when trying to boot from the harddrive I am getting the rebooting.  What is the alternate cd being discussed?  Is it just the server version?  If not, where would I find the alternate cd?

---

### Post by jameshartford on 2006-08-19
Well, I found the alternate cd, will post the results after I attempt installation.

---

### Post by jameshartford on 2006-08-21
The alternate cd also was rebooting, so I installed Ubuntu 5.10, then did the upgrade to 6.06 and it seems to be working fine now.  This was on a compaq presario 7360.

---


---
title: "virtualbox and ipod"
date: 2008-09-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by frilock on 2008-09-29
hi i have virtual box 2.0.2 and ubuntu 8.04 and im trying to get my ipod to work in virtualbox in xp i can add it in the filter section but when i boot xp and try to select it its grey and i cant click on i can mount regualr usb pen drives and mice but my ipod is a no go. i have added usb support. any ideas? (please bare with me im new at virtualbox and Linux but i can run codes and use the terminal) thank you

---

### Post by forumache on 2008-09-29
welcome to Linux, frilock

there is a problem in ubuntu with virtualbox and usb devices, i guess you solved that if you can use usb sticks in xp under virtualbox

why don't you use the rhythmbox with your ipod? it does not synchronize; but it allows to add and remove songs.

i will try to connect my ipod to virtualbox when i'll be home, although i'm using ubuntu 8.10 (almost beta). virtualbox latest is 2.0.2

---

### Post by nebosuke on 2008-09-29
It's not just the virtualbox in Ubuntu. There seems to be a general problem accessing iPods and iPhones, which is not solved yet.
Please have a loook at this ticket **[http://virtual-box.org/ticket/491](http://virtual-box.org/ticket/491)**

---

### Post by Life On Mars on 2008-10-12
It might be worth [looking at this]("http://www.davidgrant.ca/virtualbox_usb_windows_xp_guest_ubuntu_hardy") for the iPod in VirtualBox problem.

To sync your iPod in Ubuntu, why not use [Songbird]("http://getsongbird.com/")?

---

### Post by inportb on 2008-10-12
Yeah, this is a known issue. People have gotten USB devices to work in VMware that do not work in Virtualbox... but I'm not sure how well it would work with an iPod.

---

### Post by rdoolen on 2008-10-12
I have been using WinXP Pro in VirualBox on Ubuntu for almost a year. I have been using the most up-to-date versions of the applicable software; currently; iTunes 8.X, WinXpPro Sp2, VirtualBox 2.X and Intrepid beta. I synced yesterday. This has been working back to iTunes 7.X, VB 1.6 on Hardy. 

I don't know how to fix it since it always work for me, but I can share my settings with you if you tell me what you want to know.

Does your iPod even show up in Itunes?

---

### Post by Squish42 on 2008-10-26
rdoolen - I would like to see your settings for VirtualBox.

I have a similar problem to frilock's.  I ultimately fixed the 'greyed out' USB devices and I can connect USB sticks and have them show up in my XP Guest with no problem.  I can not get my iPod to show up in iTunes or in Explorer as a drive.  When I connect it for the first time it does show up as a VB device on my Ubuntu host and XP does the 'New Hardware Found' routine but nothing ever shows up.

I posted all the things I changed and my sources in the VirtualBox forum ([http://forums.virtualbox.org/viewtopic.php?p=43241#43241](http://forums.virtualbox.org/viewtopic.php?p=43241#43241)) last night.  Any help would be appreciated.

---

### Post by rdoolen on 2008-10-27
Here are my basic settings, but from reading your other post, I think your are beyond this being helpful. Post more specifics if you think I might have useful information. 

OS Type - Windows XP
Base Memory - 1024 MB
Video Memory - 32 MB
ACPI - Enabled
IO APIC - Enabled
VT-x/AMD-V - Disabled
PAE/NX - Disabled
 
Audio
Host Driver
PulseAudio
Controller
ICH AC97

Network
Adapter 1
PCnet-FAST III (NAT)
 
Serial Ports - Disabled

USB
Device Filters
0 (0 active)

Remote Display - Disabled

---

### Post by inportb on 2008-10-27
[http://www.virtualbox.org/ticket/491](http://www.virtualbox.org/ticket/491)

Apparently you could rebuild your kernel, just get the rebuilt USB module, or wait for VBox 2.1.

You could also get VMware, since they have that fixed.

---

### Post by Squish42 on 2008-10-29
inportb - Thanks for the link,
> **inportb said:**
> [http://www.virtualbox.org/ticket/491](http://www.virtualbox.org/ticket/491)

That's great news.

> You could also get VMware, since they have that fixed.

I also tried VMware Player and building a guest from scratch with easyvmx.com. I'm having the same exact problem.   I'm wondering if rebuilding the usbcore.ko will fix that too??

---

### Post by Squish42 on 2008-10-29
rdoolen - Thanks for the reply.  Unfortunately I'm still stuck.  The only differences between your settings and mine were these"
> **rdoolen said:**
> 
Base Memory - 1024 MB
Video Memory - 32 MB
IO APIC - Enabled

Audio
Host Driver
PulseAudio


I Enabled 'IO APIC' and, for kicks, change my Audio (hey, its Windows were are talking about here, it could be anything , right?)  Anyway, neither changed my results.

Maybe inportb's usbcore.ko change will help?

---


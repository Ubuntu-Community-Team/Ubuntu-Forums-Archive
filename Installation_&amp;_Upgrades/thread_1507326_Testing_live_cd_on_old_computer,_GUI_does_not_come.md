---
title: "Testing live cd on old computer, GUI does not come up"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by mfernandez on 2010-06-11
I'm trying to breathe some new life into an OLD computer so I thought I would give xubuntu a try.  I have used linux sparingly over the years so I'm pretty much clueless.  Anyway, I had tried a previous version of ubuntu on this same machine a couple years ago.  Version 7.xx I think.  That live cd would boot up into the GUI okay although it was still kind of slow.  Fast forward to now, I am trying to boot my machine from an xubuntu cd version 10.04.  The GUI does not come up and I am only presented with a terminal.  When I try to start the GUI (startxfce4) I eventually see a message that the monitor/video does not support color depth 24.  Believe it or not, I still have that older version of ubuntu so I tried it again and sure enough it still works.
 
So here is what I have noticed is different.  On the older version of ubuntu it appears to be using the 'glint' video driver.  The new version of xubuntu is using the 'vesa' driver.  I tried changing this by creating an xorg.conf file and adding a driver line specifying 'glint'.  After trying to start the GUI with that change I get an error saying that the glint module could not be loaded.
 
So finally to my question, is the glint video driver loaded by default in xubuntu?  I see it's package listed under xubuntu.  I even tried installing the package myself using apt-get and that seemed to work.  It went through some steps and did not report any errors but I still get the same error afterwards.
 
What do I need to in order to use the glint video driver with xubuntu 10.04?  Of course, the other issue is that the install does not recognize my wireless card either so there is no internet access on this machine.  Oh yeah, the video card in the machine is a 3DLabs Permedia 2 (it looks like ubuntu recognizes it as a Texas Instruments but still permedia 2).
 
Sorry for the long winded post but I would appreciate any assistance.  Thanks!

---

### Post by dino99 on 2010-06-11
since kernel 28 now X is monitored by the kernels, so you need to test with various parameter(s) on the boot line:

try: acpi=off, lapic=off; apic=off, nomodeset, irqpoll

and remove quiet splash

better to remove xorg.conf

[http://www.google.fr/search?as_q=glint%2Bubuntu%2Bxfce&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.fr/search?as_q=glint%2Bubuntu%2Bxfce&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

### Post by mfernandez on 2010-06-11
Thanks for the reply. I have actually tried some of those options already (acpi=off, lapic=off; apic=off, irqpoll). Another thing that appears to be different for me is that I am not seeing the boot menu that I see mentioned on other posts. All I get is a 'boot:' prompt. So I tried these options at that prompt. like this; boot: live apci=off etc.
 
I am assuming that I don't see the menu because of this graphics problem. I am thinking that if I could just get it to use the glint driver it might work. Is there anyway to specify which video driver to use on the boot command line?
 
I forgot to mention, I have seen posts mentioning quiet splash but I do not see that anywhere.

---

### Post by quadproc on 2010-06-11
> **mfernandez said:**
> I'm trying to breathe some new life into an OLD computer so I thought I would give xubuntu a try.
I went down a very similar path and was sorely disappointed with Xubuntu: slow, numerous application crashes, generally unusable.  Later, I found a review article that showed that Xubuntu uses more memory than standard Ubuntu!

I solved my problem by installing Puppy Linux 4.3.1 which runs well on a P3 256 MB system.  Puppy Linux does have one problem that should be mentioned: it runs as a single user system and that user, of course, is root.  Therefore, the usual protections against my doing something dumb do not apply and I am therefore extra careful on that system.

I have read little bits and pieces about Lubuntu and I think that it may be a contender in the "small old machines" class.  I will probably try it one of these days.

quadproc

---

### Post by mfernandez on 2010-06-12
I have read similar posts about xubuntu. Actually, I have just downloaded the iso for ubuntu to give it a try. As I mentioned before, the previous version of ubuntu ran on the machine. From what I have read it seems that the only (or at least the only significant) difference between xubuntu and ubuntu is the desktop environment (xfce versus gnome). If I can get ubuntu running I can also switch it to use xfce and see if it performs any better. We'll see...
 
 
I just did a quick search of lubuntu and it appears like another variant that uses the lxde desktop.  I might give it a try as well.
 
Is my assumption on these variants of ubuntu correct?  Is the only difference that they utilize different desktops?  Would it be the same to load ubuntu and just try the different desktops from within it?

---

### Post by SlidingHorn on 2010-06-12
> **quadproc said:**
> I went down a very similar path and was sorely disappointed with Xubuntu: slow, numerous application crashes, generally unusable.  Later, I found a review article that showed that Xubuntu uses more memory than standard Ubuntu!

Have you taken a look @ Lubuntu yet?  LXDE screams on my old lappy, which is a dog of a machine to begin with

---

### Post by mfernandez on 2010-06-13
Tried running the lubuntu live cd but it just gives me this error:  > (process:190): GLib-WARNING **: getpwuid_r(); failed due to unknown user id (0) It just keeps doing that like it keeps trying but keeps getting the error. ???

---

### Post by mfernandez on 2010-06-16
I finally got xubuntu running on this old machine (live, not installed yet).  I did not specify any boot options.  I let it boot up as normal into the terminal.  Then I installed the glint video driver that I downloaded from another machine (copied it to this one via usb drive) using dpkg.  Then I had to create an /etc/X11/xorg.conf file to specify using the glint driver, busid and also a few other things.  Then I entered startxfce4 and viola, here I am.

So far I like the desktop but it is still a little slow.  I assume I would pick up some speed by actually installing (versus the live version I am running from cd).  I think I will play around with this for a few days and then maybe try lubuntu.

Finally!!!!!

---


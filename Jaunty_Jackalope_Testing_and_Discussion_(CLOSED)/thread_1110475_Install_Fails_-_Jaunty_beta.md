---
title: "Install Fails - Jaunty beta"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by MountainX on 2009-03-29
I have tried to install 4 times (and I posted a prior question that didn't get a response).

The install fails at the same point every time. When I switch to the Alt-F4 terminal, here is what I see:

preseed: locale: cannot set LC_ALL to default locale. no such file or folder...
in-target: reading package lists...
in-target: the following NEW packages will be installed
Please insert the disk [Jaunty...] in drive /cdrom/

I can open another terminal (Alt-F2) and cd to, and ls the cdrom, so it is there and it can be read from.

I'm using the beta alternate installer amd64 on a computer that is currently running Hardy. I'm installing fresh to a different partition (one that used to hold Windows).

What's going on? Thanks

PS: I checked the CD. It has no defects.

---

### Post by BGFG on 2009-03-29
I had some problems with the desktop installer, checked the cd - no defects. turns out my optical drive was just hot. generally i try to keep my live cd's at 2x, just to be sure.

---

### Post by vishalrao on 2009-03-30
i believe this is listed in the "known issues"... when it mentions /dev/sdX is mounted do not press continue, press "go back" (yes its confusing) then it should work... [http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)

---

### Post by MountainX on 2009-03-30
I did receive some help at my other thread on this topic, but I want to keep this thread updated for people who find it in future searches.

1. I have burned two CDs and they both validate as good.
2. Both CDs stop at exactly the same point in the installation on this computer. See post #1.
3. Using the same installation CD in another computer works, so it is not an issue with the CD. 

Conclusion: there is a bug in Jaunty (the installer) that shows up on this hardware. Can anyone advise where to report this bug?

EDIT: filed a bug report here: [https://bugs.launchpad.net/ubuntu/+source/base-installer/+bug/351750](https://bugs.launchpad.net/ubuntu/+source/base-installer/+bug/351750)

---

### Post by mhenriday on 2009-03-31
**MountainX**, as a work-around, you could try the following : upgrade from **Hardy** to **Intrepid**, update **Intrepid**, and then upgrade from **Intrepid** to the **Jaunty** beta and update. An extra step, but in my experience it works....

Henri

---

### Post by MountainX on 2009-03-31
I'm not doing an upgrade. This is a clean install to a partition that used to hold Windows.

---


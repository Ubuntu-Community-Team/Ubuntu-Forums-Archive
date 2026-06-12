---
title: "ATI x800 XL PCIe and Karmic"
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by crjackson on 2010-04-13
Okay,  I have an eMachines W3410 that has a Radeon Xpress 200 onboard video adapter.  Karmic works okay with this but I also have an x800 XL (much faster) laying around doing nothing so I wanted to install it.

So I put the thing in the PCIe slot, then I enter the BIOS and tell it to initialize the PCIe slot for video as primary and shut down.

I switch the vga cable to the add-in card and reboot.  The card is working, I see the boot-up screens, then the grub, then the white Ubuntu emblem in the center of the screen.  The hard drive cranks a bit, then I get a flashing cursor only at the top left of the screen.

That's it.  It won't go any further.  I would really like to make use of this card if possible.  Can someone tell me how to make that happen?

Thanks

---

### Post by Mark Phelps on 2010-04-14
Just so you know, neither of these cards has ATI Linux drivers anymore because ATI dropped Linux support for them over a year ago.  So, you will most probably be using the same open source video radeon drivers that you are using right now.

---

### Post by crjackson on 2010-04-14
> **Mark Phelps said:**
> Just so you know, neither of these cards has ATI Linux drivers anymore because ATI dropped Linux support for them over a year ago.  So, you will most probably be using the same open source video radeon drivers that you are using right now.

Yes I know the closed source driver doesn't support these cards.  I just want the card to work.  Open source driver is fine.

---

### Post by drreed on 2010-04-18
> **crjackson said:**
> Yes I know the closed source driver doesn't support these cards.  I just want the card to work.  Open source driver is fine.

If you get any help with this or figure it out please let me know. I want to install compiz-fusion to do cool things w/ my xfce4 desktop environment, and all of the how-to's are for much newer ATI cards. I had problems in fedora with it too, and wound up using the default video driver that sysinstall selected, because I was getting nowhere.

My MB was designed for 2 ATI graphics cards, and I think it uses ATI chipset too.

From experience: we may have to live with this until we upgrade and get nvidia. I'll never buy another ATI product again, not anything.

---

### Post by quadproc on 2010-04-18
> **crjackson said:**
> ...
I switch the vga cable to the add-in card and reboot.  The card is working, I see the boot-up screens, then the grub, then the white Ubuntu emblem in the center of the screen.  The hard drive cranks a bit, then I get a flashing cursor only at the top left of the screen.
...
Thanks
I think that you may need to disable the onboard graphics hardware.  This would usually be done through the BIOS.

There was a problem in X windows version 1.5 where multiple video boards in a system would confuse X windows and X's response was simply to quit running without even creating a log entry.  I found a way to get around this problem: add a BusID to the primary video card's entry in xorg.conf.  I don't know if this problem still exists in X version 1.6.

quadproc

---

### Post by crjackson on 2010-04-19
It is disabled in BIOS.  I have another machine exactly like this one with an even older ATI card and it works fine.  Just the x800 PCIe won't work.

---

### Post by crjackson on 2010-04-24
Okay, I'm still trying to get some help with this.  I have found that booting to low-graphics mode everything works and looks fine (just no compiz available).

Can someone tell me how to make it load up in low graphics automatically every time so the kids can reboot this thing themselves? 

Any help would be appreciated...

---

### Post by crjackson on 2010-04-24
Well, I installed the xorg-edgers PPA and updated everything.  It didn't help anything at all.

When I try to do a normal boot,  It makes it to the splash screen and locks-up right there.  I have to do a hard reboot to recover.  

Booting to low graphics mode works pretty well (just no compiz as such).

I guess I just need to find out how to make this thing boot into low graphics mode every time.  There seems to be no other solution.

Others are running this card, so I guess they knew how to make it happen, but I don't, and no one will clue me on this TOP SECRET information.

If anyone is willing to tell me how to make the normal boot a low graphics setting I would be really grateful.

---

### Post by crjackson on 2010-05-02
> **quadproc said:**
> I think that you may need to disable the onboard graphics hardware.  This would usually be done through the BIOS.

There was a problem in X windows version 1.5 where multiple video boards in a system would confuse X windows and X's response was simply to quit running without even creating a log entry.  I found a way to get around this problem: add a BusID to the primary video card's entry in xorg.conf.  I don't know if this problem still exists in X version 1.6.

quadproc

Could you elaborate on this BusID entry.  Tell me how I find the BusID for the card, and please post either your xorg.conf or an example for me to follow.

I've gotten no where with this.  Even Lucid has the same issue.  Intrepid loves the card, but it's too dated for me.  I would love to get Karmic or Lucid using this card.

Thanks.

---

### Post by Mark Phelps on 2010-05-03
> **crjackson said:**
> ... Intrepid loves the card, but it's too dated for me.  I would love to get Karmic or Lucid using this card.

Thanks.
That's because back in the Intrepid days, you could install the fglrx video driver and get really good graphics.  

I know because I have one of the "legacy" cards that ATI quit supporting starting with Ubuntu 9.04.

You're not going to be able to get anything newer than Intrepid to use the fglrx drivers.  Like me, you're stuck using the open source drivers now.

---

### Post by quadproc on 2010-05-03
> **crjackson said:**
> Could you elaborate on this BusID entry.  Tell me how I find the BusID for the card, and please post either your xorg.conf or an example for me to follow.

I've gotten no where with this.  Even Lucid has the same issue.  Intrepid loves the card, but it's too dated for me.  I would love to get Karmic or Lucid using this card.

Thanks.
Sorry, I just found your query - hope that you didn't give up waiting on a response.

To get the BusID, do something like
```
lspci | grep VGA
```The first few numerical fields will be the BusID.  I have two cards so I get two entries:
> 02:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4870]
03:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4870]Then look in your /etc/X11/xorg.conf file for the driver entry:
```
grep "river" < /etc/X11/xorg.conf
```and look for a line which is not commented out and which specifies your graphics hardware.  In my case, it is
>     Driver      "fglrx"Then start up a text editor on the xorg.conf file and find that same line in it.  Look at the lines before and after the line that you found; the BusID needs to be located in the same section as the Driver line.  Here is that part of my xorg.conf file:
```
Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:2:0:0"
EndSection
```When you are ready to put the modified xorg.conf file back, you will need to be privileged.  You can do this several ways; one easy way is to save the modified file in your directory somewhere and then use sudo cp <newfile> /etc/X11/xorg.conf.  I suggest making a backup copy of your existing xorg.conf file before you start, in case you need to revert to the original for some reason.

One additional note: from reading the forums in the last few days I gather that Lucid has lots of graphics problems.  It looks like some of those problems relate to situations similar to yours.  I would wait until things settle down and the Lucid bugs get worked out before trying to switch to it.

I hope that this helps.

quadproc

---

### Post by crjackson on 2010-05-03
> **Mark Phelps said:**
> That's because back in the Intrepid days, you could install the fglrx video driver and get really good graphics.  

I know because I have one of the "legacy" cards that ATI quit supporting starting with Ubuntu 9.04.

You're not going to be able to get anything newer than Intrepid to use the fglrx drivers.  Like me, you're stuck using the open source drivers now.

Sorry Mark, you missed the part where I'm not trying to run fglrx drivers.  I'm hanging up with the open source drivers.

I installed an even older card than the x800 xl today, I installed an x300 and it works perfectly.

There is something about 9.04 and above that doesn't like this hardware combination.  The card works fine, but not on these 2 identical machines if running 9.04 or above.

---

### Post by crjackson on 2010-05-03
> **quadproc said:**
> Sorry, I just found your query - hope that you didn't give up waiting on a response.

To get the BusID, do something like
```
lspci | grep VGA
```The first few numerical fields will be the BusID.  I have two cards so I get two entries:
Then look in your /etc/X11/xorg.conf file for the driver entry:
```
grep "river" < /etc/X11/xorg.conf
```and look for a line which is not commented out and which specifies your graphics hardware.  In my case, it is
Then start up a text editor on the xorg.conf file and find that same line in it.  Look at the lines before and after the line that you found; the BusID needs to be located in the same section as the Driver line.  Here is that part of my xorg.conf file:
```
Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:2:0:0"
EndSection
```When you are ready to put the modified xorg.conf file back, you will need to be privileged.  You can do this several ways; one easy way is to save the modified file in your directory somewhere and then use sudo cp <newfile> /etc/X11/xorg.conf.  I suggest making a backup copy of your existing xorg.conf file before you start, in case you need to revert to the original for some reason.

One additional note: from reading the forums in the last few days I gather that Lucid has lots of graphics problems.  It looks like some of those problems relate to situations similar to yours.  I would wait until things settle down and the Lucid bugs get worked out before trying to switch to it.

I hope that this helps.

quadproc

Thanks for the information.  I ordered an x300 card from eBay and it arrived today.  I knew that one would work because I put one in the sister machine.

I popped it in and viola.  It worked as expected.  I really liked the x800 card and I'm not going to give up. I really want to figure this thing out, and file a proper bug report.

---

### Post by quadproc on 2010-05-04
> **crjackson said:**
> Thanks for the information.  I ordered an x300 card from eBay and it arrived today.  I knew that one would work because I put one in the sister machine.

I popped it in and viola.  It worked as expected.  I really liked the x800 card and I'm not going to give up. I really want to figure this thing out, and file a proper bug report.
Excellent!  Please let us know how things work out. I remain very interested in the graphics/system interface and compatibility issues of systems in general.

quadproc

---


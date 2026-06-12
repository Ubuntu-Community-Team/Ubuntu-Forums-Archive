---
title: "Broken"
date: 2008-12-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dakkar9999 on 2008-12-09
Last series of update has broken my installation.  Now it just hangs on boot.  Going in safe mode, I can read the lines until "checking battery state...  OK"  then it hangs.  My PC is a desktop, no laptop.  Not sure if the checking the battery message should be there...

Tried the different boot options, nothing so far. 

Suggestions?

---

### Post by ShirishAg75 on 2008-12-09
dakkar9999, 
      even if I have a desktop and yes, it also does talk about battery while booting up (both in Intrepid as well as in Jaunty). 

I would theorize it two ways with no idea which one is correct although I believe both might be correct. 

a. Ubuntu is supposed to be using upstart - an event based replacement for /sbin/init daemon although they have not started working on the same. 

FWI understand, eventually it would be like a plug-and-play mechanism so depending on what things you have under the hood those services would start up or not making for a lean and mean booting experience. 

b. Desktop's also have a battery, the battery which is in BIOS which keeps track of date and many other things. It might be checking for this as well.


Now as far as booting is concerned, I'm hoping you have edited your boot lines so 'quiet' and 'splash' are taken out. Instead of that put 'verbose' therein. It should give you a sort of more in-depth idea of what's happening and where its hanging. Then you can file a bug of not booting against the grub package giving the output just before it hangs . A little bit about the hardware you have would also give the developers an idea what's wrong with it.

---

### Post by |{urse on 2008-12-09
Its hanging on acpi. Try pressing E at the grub menu and add acpi=off to the kernel parameters (just type acpi=off at the end of the line). Please post back and let us know if this worked for you.

---

### Post by dakkar9999 on 2008-12-10
Nope, that didn't work.  The screen just goes blank and there is no activity.

If I do a normal boot, the progress bar goes almost entirely full, then it hangs.  But something strange happens, which might give an indication of the problem.  There is a green dotted lines that appears under the progress bar.  It kind of flicker and then becomes solid.  It would seem to hint at some graphic card hang up, but I'm not sure...

Suggestions?

---

### Post by |{urse on 2008-12-10
is there any way you could try a different monitor?

---

### Post by autocrosser on 2008-12-10
Next thing to do is:

as root, edit your /boot/grub/menu.list--take the main kernel line & where it says "quiet splash"--change it to "nosplash". Use a LiveCD to get to it--mod the file & then reboot. You will get the verbose text boot & then post with the info from when it hangs.

---

### Post by |{urse on 2008-12-10
...

---

### Post by dakkar9999 on 2008-12-11
Ok, I've got it working again.  Not sure if it'll be back on at reboot though...

I went through the recovery boot, Did the X display fix (or something like that) still went black at boot, but when I did ctrl+alt+del, it dropped me to the session login, from  which I was able to load the desktop.

So I guess I'll have to reboot to see if it's fixed or not...

---

### Post by dakkar9999 on 2008-12-11
Yeah, it's the ATI driver that's acting up.  If it is deactivated, I'm able to  log in.

---

### Post by jerrylamos on 2008-12-11
> **dakkar9999 said:**
> Last series of update has broken my installation.  Now it just hangs on boot............... 

Suggestions?

Suggestions?  OH, YESS!!  CAN THE UPDATES!

I've been on Intrepid since pre-Alpha and Jaunty since pre-Alpha.  Things will be crippling along, getting somewhere, then WHAM! an update kills me.  In August an Intrepid "Update" killed Intel graphics.  They didn't fix that until after release over 2 months later, and that by just disabling Compiz.  I'd do an "UPDATE", i.e. poison pill, it wouldn't even boot, so I had to go back to the last running CD Live.

Jaunty same thing.  Early Alpha ran, an UPDATE killed me, wouldn't even boot.

Being burnt and fried, now I download a CD Live.  If it runs, I'll cautiously install on a dual boot.  If it doesn't run, forget it.
I DON'T UPDATE ANYTHING!

Today's CD Live installed and immediately wanted to do 230 updates.  NO WAY!!  20081211's running on 4 machines and not about to kill them with updates.


Jerry

---

### Post by autocrosser on 2008-12-11
So Jerry---why are you doing testing?  If you want a stable system--keep Hardy around & you won't have the problems. And if noone installs updates--who is testing them?

I "thought" the point of a testing system is to test new software & ways to use hardware--Which means that things break--When it breaks--bug report it & move on. I work with the developers (sometimes very close) to get problems that matter to me fixed & have a very good success rate.

Take a look around in this forum & you will find a large group of risk-takers that actively help the developers along--& most of us have had major & minor breakage frequently during the Alpha stage--I feel very comfortable about fixing my system & am not afraid to try anything new. I also work hard to help anyone that needs it.

My advice to you is to decide if you really want Alpha-class software on your systems--if stability is paramount, use a stable release.

---

### Post by ShirishAg75 on 2008-12-11
Lemme add a bit to what autocrosser says. 

Its never a good idea to just pull updates. What I usually do is do 

```
$ sudo aptitude update
```

and then do 

```
$ sudo aptitude safe-upgrade
```

Now when I am doing an upgrade I do atleast have a cursory look (actually more than cursory look) and see what updates I have. I had 100 updates from yesterday which were basically gcc and its pals, openjdk and its brethen and then little bit of mesa stuff.  All of which btw is also known on the jaunty-changes mailing list (which I keep checking in as well) . 

Now for last 2 days I didn't hear anything bad about gcc so that was good, none of other packages have anything to do either with booting up or with the networking so did it. 

The only time I don't strictly update is when network-manager or any of the boot packages (say grub) new have been released. 

Apart from that, unlike your experience I have experienced pretty good catches by forum-users and developers (where a certain update would disable updation or boot) . Been saved atleast 2-3 times although if I had to reinstall the system wouldn't have thought twice about it. That's the whole point of testing. To see what breaks and breaks where. 

But the least the developers need to know where it breaks. Without our help as guinea pigs they would never know that for they haven't got 

a. A wide variety of hardware
b. Different ways in which a user may brick the system. 

Automated testing may help but only so far. 

That's my 2 paise :)

---

### Post by dakkar9999 on 2008-12-12
Well, I don't do any work on that machine, so it's ok.  I don't mind being a  guinea pig!  

But does anyone have any suggestion for the ATI driver causing problem?  Or should I just sit  tight and wait for the next updates?

---

### Post by Gina on 2008-12-12
I never do a "Partial Update" using update manager - I wait until all required packages are available.  I sometimes use update manager and sometimes Synaptic - in either case carefully checking what it proposes doing before going ahead.  This at least stops unnecessary breakage caused by incomplete package uploads.

I have 2 machines I regularly use and which default to Jaunty and get updated daily (usually) - an AMD64 desktop running 64bit Jaunty and a laptop running 32 bit Jaunty.  So far I've had only very minor problems - but it's very early days yet.

I am quite happy reporting bugs and applying fixes or if there's a disaster I'm happy to reinstall.  I've installed various versions of Ubuntu dozens if not hundreds of times and it's second nature to me.  Sometimes I reinstall just to tidy up.

I must add a +1 to autocrosser et al that if anyone wants to do testing they must apply the updates and must report any problems in launchpad (where the developers look for feedback).  Otherwise, if someone isn't happy to fix a broken system they should stick to a normal release.

---

### Post by autocrosser on 2008-12-12
> **dakkar9999 said:**
> Well, I don't do any work on that machine, so it's ok.  I don't mind being a  guinea pig!  

But does anyone have any suggestion for the ATI driver causing problem?  Or should I just sit  tight and wait for the next updates?

I would wait--the devs are almost wrapped up this week in Mountain View (I really wish I had gone--I live 5 hours from there--OT) & will be ready to work next week....Have you bug reported the problem? I've had a few small problems with Xorg & I would bet from what I have heard that Xorg will be getting a lot of love real soon.

And as the ATI driver is now "open", you will see some great strides very soon---hang in there----

---

### Post by dakkar9999 on 2008-12-12
Thanks for the update!

---


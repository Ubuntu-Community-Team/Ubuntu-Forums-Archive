---
title: "GRUB was messed up by Windows"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by Adola on 2008-10-19
[FONT="Comic Sans MS"]Hi there!

I'm writing this to help people with similar problems...
This is an easy fix and works!

My name is Adam.  And I'm new to Ubuntu because I've been on Windows for so long. 

But, I'm breaking free!!

HOWEVER, I am a gamer..And, I need Windows as well. :/
(Yeah, I know...Wine..But...I'm sorry..It just doesn't work as well as the real thing.....)

Anyway, I've recently come about some problems with Dual-Booting.


I'll set up the scenario. 

I bought an extra harddrive for my computer.
So I could set up a dual-boot with XP and Ubuntu 8.04 Hardy Heron. 

So...
I installed XP first...On the smaller harddrive.  (I set it to secondary.  As, Ubuntu was what I primarily used) Then, on the new bigger harddrive.  Installed Ubuntu :D

EVERYTHING WAS GREAT...(Aside from the Linuxant Audio issues o.O) But, nonetheless, everything went as it should :D

THEN...As most users should/have to. I had to reinstall windows about 3 months down the road. 

So...When I did...I couldn't choose to load Ubuntu...
~GASP~
So.  After MUCH searching.  I found this [/FONT]

```
sudo grub
find /boot/grub/stage1
root (hdX,x)
setup (hdX)

*replace (X,x) with what you got with "find /boot/grub/stage1"
```


[FONT="Comic Sans MS"]But of course...That didn't work....

HOWEVER, I made it work...With a typo :D

What I'm about to tell you...Worked for when I had to reinstall Windows on on harddrive..By wiping it and installing a fresh copy of Windows on it...

It ALSO worked for when I re-wiped it.  And installed Vista on the same harddrive...

So bascially..What I'm telling you is this...

The mistake I made.  Worked for XP, and Vista. 

Here it is...


Take your Ubuntu LIVE Cd 8.04 and put it in your computer...
Reboot..
Of course, if it doesn't go into the "test or install" thing for Ubuntu..

You will need to change your BIOS boot order to allow CD/DVD's to boot first..

Ok...When you finally get the LIVE cd running...

As to say, are able to work in the "Test" enviroment..
Like..DON"T INSTALL IT..But, just "Try it without any changes to your computer"

From there.  up at the top of the screen notice "Applications, Places, System"

Click "Applications" then, Accesories, then Terminal..

And do this 

```
sudo grub
find /boot/grub/stage1
root (hdX,x)
setup (hdX)

*replace (X,x) with what you got with "find /boot/grub/stage1"
```

Then, reboot...

If that DOESN"T work.  And you boot right into Vista, or XP..
Then REDO all of that..Put the LIVE CD back in..And test it again...Untill you get back at Terminal...

Now...Try variants...
Like...
For me.
I had to 
```
sudo grub

root (hd1,0)
setup (hd1)

```

And..I know it sounds dumb..But just keep trying..

Keep trying different combonations..Like

"root (hd0,1)
setup (hd0)"

But, you will know if a combonation doesn't work or not because you will get an error...

Eventually..You WILL restore GRUB..

I promise..It took me a few tries..But, it happend..

I only say "try different" combo's..
Because..I don't konw your system...And, what HD's you have set as what..So...Yeah..


Again..I'm a newbie at Ubuntu..But, I'm trying..And I hope this helps someone a LITTLE

Ask me anything..
But, I am on Dial-up..So...Don't expect a LIGHTNING fast response...

Thank you for reading. 

:D




(Also, if you are on Dial-up.  And have the strangest Audio problems with ALSA and can't get your sound to work no matter what...contact me...I had the same problem for MONTHS..It's a REALLY simple fix that's hard to find using google...Because the errors point to OTHER problems than what it really is.  Thanks!)
[/FONT]

---


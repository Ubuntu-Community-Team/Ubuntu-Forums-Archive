---
title: "Compiz is broken with latest compiz update?"
date: 2009-04-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by binbash on 2009-04-18
I tried with 3 different kernels but it is broken (it was working perfect).I am getting this error : 

compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Failed to read saved session file /home/nyn/.config/metacity/sessions/105c13304cc7922b1c124005480351046900000034030001.ms: Failed to open file '/home/nyn/.config/metacity/sessions/105c13304cc7922b1c124005480351046900000034030001.ms': No such file or directory

---

### Post by Jim March on 2009-04-18
Yuppers.  Same here.

> jim@thecritter:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 


I'm running an Intel 965 video (aka x3100).  I'm not doing UXA in case that matters.  Ideas?

---

### Post by eprenen on 2009-04-18
Same here! Sucks :(

---

### Post by tjeremiah on 2009-04-18
I did an update last night. Just turned on notebook and compiz fails to enable :(

---

### Post by tjeremiah on 2009-04-18
This is the alert I get now when first presented the desktop :

---

### Post by ktp on 2009-04-18
> **binbash said:**
> I tried with 3 different kernels but it is broken (it was working perfect).I am getting this error : 

compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Failed to read saved session file /home/nyn/.config/metacity/sessions/105c13304cc7922b1c124005480351046900000034030001.ms: Failed to open file '/home/nyn/.config/metacity/sessions/105c13304cc7922b1c124005480351046900000034030001.ms': No such file or directory

Looking at the change log:

> * debian/patches/028_compiz_manager_blacklist:
    - blacklist GM965 (8086:2a02) until the freeze with the intel
      driver is fixed (LP: #359392)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392)

---

### Post by chrisccoulson on 2009-04-18
> **Jim March said:**
> Yuppers.  Same here.

I'm running an Intel 965 video (aka x3100).  I'm not doing UXA in case that matters.  Ideas?

Your card has been blacklisted until [this bug]("https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392") is fixed.

---

### Post by labinnsw on 2009-04-18
I am surprised to find out that compiz was only broken with the last update. I thought it had always been broken. I frequently come up on fixes for other applications which simply involve disabling compiz. Another thing is that a 2 x 2 window swithcher will only fit in a 1 x 2 space when compiz is enabled.

Occasionally I enable it to see a little window dressing but when I am about to start working I disable it.

---

### Post by sports fan Matt on 2009-04-18
Im glad I checked..I dont think I should install updates just yet...However Id like feedback on my decision..

---

### Post by Teamgeist on 2009-04-18
My Compiz worked just fine, but is now disabled by default.
To reactivate Compiz on the Intel GM965 you will have to do the following.

```
sudo gedit /usr/bin/compiz-manager
```

Look for the section that starts with:

```
# blacklist based on the pci ids 
```

Put an # in front of

```
T="$T 8086:2a02 " # Intel GM965
```

so it looks like this:

```
#T="$T 8086:2a02 " # Intel GM965
```

Save the file, lock out and back in and compiz should be running just like before. If logging out does not do the trick for you, try rebooting.

Cheers!

---

### Post by Bios Element on 2009-04-18
> **Teamgeist said:**
> My Compiz worked just fine, but is now disabled by default.
To reactivate Compiz on the Intel GM965 you will have to do the following.

```
sudo gedit /usr/bin/compiz-manager
```

Look for the section that starts with:

```
# blacklist based on the pci ids 
```

Put an # in front of

```
T="$T 8086:2a02 " # Intel GM965
```

so it looks like this:

```
#T="$T 8086:2a02 " # Intel GM965
```

Save the file, lock out and back in and compiz should be running just like before. If logging out does not do the trick for you, try rebooting.

Cheers!

Ya know...I imagine they blacklisted it for a good reason...

---

### Post by tjeremiah on 2009-04-18
should I do this ^ or wait for a fix/update?

---

### Post by Amaranth on 2009-04-18
Better way:

[http://ubuntuforums.org/showthread.php?t=582112](http://ubuntuforums.org/showthread.php?t=582112)

It seems if you use UXA you aren't affected by the bug that this was blacklisted for but of course that has other problems...

EIther way, if X freezes while running compiz on these chips just remember that is why it is blacklisted.

---

### Post by tjeremiah on 2009-04-18
well, there was never any freezes, just screen tearing here and there.

---

### Post by ktp on 2009-04-18
> **tjeremiah said:**
> well, there was never any freezes, just screen tearing here and there.

But that does not mean there is no issue.  You can always disable the check at your own risk.  It's better to be safe, from the Ubuntu's point of view, until the issue is fixed.

---

### Post by tjeremiah on 2009-04-18
so ill wait till its fixed.

---

### Post by bonsiware on 2009-04-18
fusion-icon --> right click --> reload window manager

it works for me!

---

### Post by binbash on 2009-04-18
fusion-icon works fine BUT it sucks at start up with docky! I am using UXA so i am not affected i guess.Anyways i am gonna try Teamgeist's way.

---

### Post by Teamgeist on 2009-04-18
Yeah I use UXA myself and never had issues. So I had to un-blacklist it to be able to use Compiz at all.

---

### Post by ghindo on 2009-04-18
Well, shoot.  I guess I understand why the decision was made (my machine using the Intel chipset froze up quite a few times), but I find it kind of odd how late in the development cycle the decision was made.  Here's to hoping that Intel performance is awesome in Karmic!

---

### Post by tjeremiah on 2009-04-18
what is this Karmic you speak of?

---

### Post by wipeout140 on 2009-04-18
> **tjeremiah said:**
> what is this Karmic you speak of?

Ubuntu 9.10 - Karmic something is the code name

---

### Post by ghindo on 2009-04-18
> **wipeout140 said:**
> Ubuntu 9.10 - Karmic something is the code nameKarmic Koala ;)

---

### Post by tjeremiah on 2009-04-18
> **Teamgeist said:**
> My Compiz worked just fine, but is now disabled by default.
To reactivate Compiz on the Intel GM965 you will have to do the following.

```
sudo gedit /usr/bin/compiz-manager
```

Look for the section that starts with:

```
# blacklist based on the pci ids 
```

Put an # in front of

```
T="$T 8086:2a02 " # Intel GM965
```

so it looks like this:

```
#T="$T 8086:2a02 " # Intel GM965
```

Save the file, lock out and back in and compiz should be running just like before. If logging out does not do the trick for you, try rebooting.

Cheers!
funny, but everything is already the way you put it and it doesnt work. but now I already know the reason. Heres hoping for an update :(

---

### Post by tjeremiah on 2009-04-18
Actually, this code forces compiz to work again even though your card is blacklisted :

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

---

### Post by novafluxx on 2009-04-18
I wasn't having any problems, not compiz is disabled lol, nice.

Thats the price we pay for 'stability' I guess. I wasn't having ANY issues, do a normal update, and poof, there goes a feature...

Why not just tell the people WITH problems to turn compiz off, instead of blacklising the damn driver for EVERYONE...

Thanks...better be fixed by release.

---

### Post by ren48185 on 2009-04-19
> **Teamgeist said:**
> My Compiz worked just fine, but is now disabled by default.
To reactivate Compiz on the Intel GM965 you will have to do the following.

```
sudo gedit /usr/bin/compiz-manager
```

Look for the section that starts with:

```
# blacklist based on the pci ids 
```

Put an # in front of

```
T="$T 8086:2a02 " # Intel GM965
```

so it looks like this:

```
#T="$T 8086:2a02 " # Intel GM965
```

Save the file, lock out and back in and compiz should be running just like before. If logging out does not do the trick for you, try rebooting.

Cheers!

I tried this and without fail it completely froze the desktop 3 times in a row. Compiz still works great on my desktop with NVIDIA but not with the Intel GM965 on my laptop. I hope it will be fixed by the next update...

---

### Post by Vorian on 2009-04-19
> **novafluxx said:**
> 
Thanks...better be fixed by release.
or what?

---

### Post by novafluxx on 2009-04-19
Or nothing, It'll just look bad for Ubuntu.

I've been running Jaunty since Alpha 5 or 6, and haven't had a single issue. Then just after the RC is released, they break my compiz...

Why wasn't this fixed in, oh I don't know, alpha or beta?? Why did it wait until AFTER the RC was released lol

If its not fixed by release, will it be fixed post release or will the users with Intel graphics be left without compiz for 6 months? Just an honest question.

---

### Post by biji on 2009-04-19
Just updated........ and compiz not working also :(

---

### Post by nwadams on 2009-04-19
this will get fixed asap. this is the kind of problem that if it affected everybody instead of just intel it would delay a release.

---

### Post by chrisccoulson on 2009-04-20
> **novafluxx said:**
> 
Why wasn't this fixed in, oh I don't know, alpha or beta?? Why did it wait until AFTER the RC was released lol

It wasn't fixed before because the problem was only just reported. It will likely be fixed with an update after release.

---


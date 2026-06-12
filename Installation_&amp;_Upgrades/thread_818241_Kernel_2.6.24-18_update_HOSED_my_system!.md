---
title: "Kernel 2.6.24-18 update HOSED my system!"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by ohiomoto on 2008-06-04
UPDATED---HOSED AGAIN!!!!!!
see page 8


Installed available updates this morning and my system is hosed.

1.  System won't shut down properly.  After hitting the "power" icon the system hangs on a blank desktop.[LIST]
[/LIST]  I have to power down the computer shutdown.

2.  I have to get online "manually".  Once I get online networking returns to normal.

3.  Firefox--lost all bookmarks and the ability to use bookmarks.  But history is still available.

4.  Firefox-- Won't browse "Back" or "Forward". 

Tried booting to kernel 2.6.24.-17 with the same results.

Anyone else run into these problems?

Best way to resolve the issue?

Reinstall 8.04 (or maybe 7.10 would be a better idea:( )?

---

### Post by ohiomoto on 2008-06-04
> **ohiomoto said:**
> Installed available updates this morning and my system is hosed.

1.  System won't shut down properly.  After hitting the "power" icon the system hangs on a blank desktop.[LIST]
[/LIST]  I have to power down the computer shutdown.

2.  I have to get online "manually".  Once I get online networking returns to normal.

3.  Firefox--lost all bookmarks and the ability to use bookmarks.  But history is still available.

4.  Firefox-- Won't browse "Back" or "Forward". 

Tried booting to kernel 2.6.24.-17 with the same results.

Anyone else run into these problems?

Best way to resolve the issue?

Reinstall 8.04 (or maybe 7.10 would be a better idea:( )?

Okay, I think I solved my problems.  I really didn't know what I was doing, but I was willing to take a chance because my install was relatively fresh and I had no data on the partition.  

I simply opened up Synaptic Package Manager and removed all previously installed kernels.  Read the descriptions carefully and they will advise you to remove the "generic" kernels. So I went and found all of the "old" generic kernels that were marked (installed) and marked them for removal.  These are the same kernels listed in the GRUB menu at boot.  I restarted my system and everything has been restored to normal (I HOPE!).  The only noticeable difference is that kernel 2.6.24.-18 is the only one listed in my GRUB menu now.

I'll post any further updates if I run into any other problems, but it looks like I got lucky.

I hope this helps clue someone in on what the real problem with this update.

Good luck.

Tim

---

### Post by steveneddy on 2008-06-04
OK, Tim.

Good luck. we're all counting on you!

---

### Post by ohiomoto on 2008-06-04
Counting on me to what...F my system up?  lol

Seriously, is removing kernels a common practice?

I just found this thread: [http://ubuntuforums.org/showthread.php?t=818387](http://ubuntuforums.org/showthread.php?t=818387)

It seems like it's something a lot of people do anyway.

---

### Post by tgrimley on 2008-06-04
Don't see any compelling reason to delete old kernels unless you're that worried about diskspace.  Sometimes they come in handy.

---

### Post by ohiomoto on 2008-06-04
> **tgrimley said:**
> Don't see any compelling reason to delete old kernels unless you're that worried about diskspace.  Sometimes they come in handy.Not worried about space.  Never took a 7.04 or 7.10 kernel off my other laptop.  Hell, I didn't even know you could. I was just grasping at straws here.

I have no idea why, but everything works perfectly now.  Dual booting, remote desktops, IDEs, media players, firefox, NAS....it's all good again.  Seems like the new kernel didn't like the old kernel.  Something had to give and I guess I got lucky.

I don't keep much on my OS partition because I don't want my OS to be a full time hobby. I just want it to work. So I'm not one to dilly dally around much.  If I can't get it working quickly or mess it up trying, I'll just reinstall the OS.  I never had an issue with Ubuntu before.  Overtime, I'll probably learn how to "fix" things and know why it worked.

---

### Post by bapoumba on 2008-06-04
I usually keep the previous working kernel, just in case :)

---

### Post by cespinal on 2008-06-04
problem solved!!!

thank you Ohio!!!!!

Just deleted the previous generic kernels and thats it! 

YIPEEEE

---

### Post by ohiomoto on 2008-06-04
Cool!  It fixed this one too: [http://ubuntuforums.org/showthread.php?t=818608](http://ubuntuforums.org/showthread.php?t=818608)

---

### Post by mtantawy on 2008-06-05
thanks , i installed all the updates, seems my fault, but why r those updates listed while they are not final??
and what is meant by "generic" is it like BETA??

thanks again,
Mahmoud Tantawy

---

### Post by ohiomoto on 2008-06-05
> **mtantawy said:**
> and what is meant by "generic" is it like BETA??No, I think it means they are the "basic" or "general" kernel.  I'm sure someone can correct me or add a better explanation.

---

### Post by mtantawy on 2008-06-05
> **ohiomoto said:**
> No, I think it means they are the "basic" or "general" kernel.  I'm sure someone can correct me or add a better explanation.
if it means basic or general, why it cracked all our systems??? :S

---

### Post by Bald.asm on 2008-06-05
hey, I am new to this and well just feeling my way around. does anyone know how to perform a manual install on hla. i used the auto set up but it is not working, oh yea i am using windows 32bit. any help would be appreciated. i would also like to know how to make my own thread on this subject, but right now running a little short on time. thanks.:guitar:

---

### Post by ohiomoto on 2008-06-05
Sorry to break the news, but the problems are back.

I did another update today and things went bad again!

Most of the packages seemed harmless, but one of them brought all of the bad behavior back.  Maybe the dpkg??

Anyway, I might mess around with it a little more, but will probably just reinstall 8.04 or go back Ubuntu 7.10 until this gets resolved.

Any other ideas???

---

### Post by ohiomoto on 2008-06-05
SORT OF!!

I shouldn't say "SOLVED",  "temporarily fixed" is probably more appropriate.

Okay, I removed all of the old "kernel headers".  So everything on my system is pure 2.6.24-18 (I think).  After reboot, everything seems normal again--for now.  (I'm sure I'll be FUBAR'ed with the next set of updates.)

I had to reboot form the terminal (sudo reboot) because my "power icon/button" was still acting up causing my system to hang.  If you don't get a little description while hovering over the button it means it's not functioning properly.  Once rebooted, everything works perfectly(I think)!

So here is the real question:  Can anyone make sense of this?  Could it be that the 2.6.24-18 kernel headers aren't lined up properly?  (I don't know what that means, but I heard "my headers aren't lining up" before.)  Someone has to be able to SOLVE this!

---

### Post by bkline on 2008-06-05
> **ohiomoto said:**
> Sorry to break the news, but the problems are back.

I did another update today and things went bad again!

Most of the packages seemed harmless, but one of them brought all of the bad behavior back.  Maybe the dpkg??

Anyway, I might mess around with it a little more, but will probably just reinstall 8.04 or go back Ubuntu 7.10 until this gets resolved.

Any other ideas???

If I were in your shoes, and especially if the alternatives I was facing were as drastic as a fresh installation of the OS, possibly even dropping back to Ubuntu 7.10, then I would be tempted first to try reinstalling 2.6.24-17 (possibly combined with uninstalling 2.6.24-18) and running that kernel, which was working perfectly well before the fateful update.  I realize that it's still too early to declare victory, but I've been running for over 24 hours without a ripple after dropping back to the previous kernel version.

---

### Post by sports fan Matt on 2008-06-05
Would it also be wise to delete "splash and "quiet" from the boot menu for a text only console to see where its hanging?

---

### Post by ohiomoto on 2008-06-05
If I want to put 2.6.24-17 back on, do I simply install the kernel and all of the headers in synaptic?  Then reboot to 17 and remove 18?  

I'll see how it goes, but it would be nice not to need a full install.  I would like to keep my bookmarks and current software packages.


> **sox fan Matt said:**
> Would it also be wise to delete "splash and "quiet" from the boot menu for a text only console to see where its hanging?Not sure how to do that.  I figure I will see this problem again at the next update.  lol

---

### Post by bkline on 2008-06-06
> **ohiomoto said:**
> If I want to put 2.6.24-17 back on, do I simply install the kernel and all of the headers in synaptic?  Then reboot to 17 and remove 18?

Sounds about right.  I'm still having difficulty understanding why removing 18 should be necessary, but if it works, it would be hard to say it was the wrong thing to do.  I've never done this (never been bold enough to purge kernels the distro maintainers felt I should keep around as a safety net), so you probably want advice from someone with more experience in this area than I bring to the table.  However, if no such advice appears, and you're going to scrub the disk and start from square one otherwise, how could it hurt to try?

---

### Post by ohiomoto on 2008-06-06
Maybe I'll try it just to see what happens.  I'll leave 18 on for now and see if it blows up again.

I must admit, when 18 is running correctly, it's pretty snappy.

---

### Post by ohiomoto on 2008-06-06
Okay running on 2.6.24-17-generic again.  

1. I had to add the kernel and all headers and reboot.
2. System was hosed.
3. Removed 2.6.24-18-generic.  Did complete removal.
4. System was still hosed.
5. Took out all -18 headers.  
6. System A-Okay! (But slightly slower I believe.)
So it seems to me that there is a conflict with the headers.

The next test will be to try and do the -18 update again...

---

### Post by ohiomoto on 2008-06-06
Okay, put -18 back and now 2.6.24-18 starts in low graphics mode but 2.6.24-17 boots fine.
```
sudo apt-get update
sudo apt-get install linux-image-2.6.24-18-generic
sodu reboot
```

---

### Post by mridkash on 2008-06-06
New kernel updates (>16) broke suspend and hibernate on my pc. The system goes to suspend, but never wakes up :-k
I'm back on 16. suspend works now, but is it safe to run older kernels?

---

### Post by ChameleonDave on 2008-06-06
I feel your pain!

I too have just done this update on one of my machines, and it stopped me getting as far as KDM!

It gives me this error:
```

yume login: [  108.874475 uarts_close: bad serial port count; tty->count is 1, state->count is 0
```

To get to my desktop, I have to log into the terminal and manually start GDM.

I am now going to try removing old kernels and headers, as you did, in the hope that it will fix it.

---------

Update: nope, it didn't fix it.  I'm now trying to upgrade to 19, which is in the repos.  It will take a long time, because I am on dial-up today.

---------

Update: Argh!  On my other machine, which was working fine, I decided to pre-emptively remove all old kernels and headers just in case they caused problems with updates.  Now I can't start X at all!  I've had to boot into XP to post this.

---

### Post by ohiomoto on 2008-06-06
I think I got it this time!

I was able to get the 2.6.24-18 kernel running while keeping the 2.6.24-17 on the machine.  Both Kernels are working normally.  

The solution...simply remove any old header packages. It appears that the old kernels have no effect on the new kernel.  At the present time, I do not have header packages installed and everything works fine. (I'll try adding the generic header package later.)

In addition I made sure I had the following packages:```
linux-image
linux-image-2.6.22-18-generic
linux-image-generic
linux-restricted-modules
linux-restricted-modules-2.6.22-18-generic
linux-restricted-modules-generic
linux-ubuntu-modules-2.6.22-18-generic
```

I used synaptic package manager to complete the task.

I hope this helps someone figure out the root of the problem.

---

### Post by ohiomoto on 2008-06-06
> **ChameleonDave said:**
> I am now going to try removing old kernels and headers, as you did, in the hope that it will fix it.

---------

Update: nope, it didn't fix it.  I'm now trying to upgrade to 19, which is in the repos.  It will take a long time, because I am on dial-up today.

---------

Update: Argh!  On my other machine, which was working fine, I decided to pre-emptively remove all old kernels and headers just in case they caused problems with updates.  Now I can't start X at all!  I've had to boot into XP to post this.Sorry for your troubles.  I was going to suggest that you try the headers only and see what happens.  If it makes you feel any better I'm sure I'll be hosed again later today.  lol

Seriously, have you tried the recovery kernel at boot?  You should be able to fix your X problem there.  

Good Luck

---

### Post by ohiomoto on 2008-06-06
I installed the linux-header-generic package and brought back all of the problems.  I then removed them and it looks like everything is back to normal.  It looks like the -18 kernel doesn't like header packages.

What do the headers do anyway?  Are they included in the linux-image?


> **mridkash said:**
> New kernel updates (>16) broke suspend and hibernate on my pc. The system goes to suspend, but never wakes up :-k
I'm back on 16. suspend works now, but is it safe to run older kernels?
I'll check into the suspend and hibernate.  I did confirm that the -18 kernel is running 10-15 frames per second faster than the -17 kernel.

---

### Post by ohiomoto on 2008-06-06
Hibernate and suspend work.  Hibernate seemed little slow to wake, but I never use it on any of my laptops so what do I know.  This is a 32-bit install on a Dell Vostro 1400.

The litmus test will come with the next round of updates.  lol

---

### Post by Dale61 on 2008-06-06
If it helps, I have the following installed:
linux-headers 2.6.24-16 + generic
linux-headers 2.6.24-17 + generic
linux-headers 2.6.24-18 + generic
linux-headers-generic
linux-image-2.4.24-15-generic
linux-image-2.4.24-16-generic
linux-image-2.4.24-17-generic
linux-image-2.4.24-18-generic
linux-image-686
linux-image-generic

as well as the restricted modules for same, and ubuntu modules.

My system is running without a problem, and all updates go smoothly and flawlessly.

Of the above, can any be removed, or is it best to retain them?  Hard drive space is not a problem at this stage as I have 68GB remaining (out of 82).

---

### Post by ChameleonDave on 2008-06-06
Aha!

All the meta-packages (such as *linux-headers-generic*) point to the 2.6.24-18 version of things, but I've checked the repos, and 18 is not actually the latest one; 19 is.

So, since 18 screwed my system, I decided to upgrade to 19 rather than roll back to 17.

It seems to be important to make the version of all the packages match up nicely.

Line breaks inserted for clarity:

```
$ sudo -s
$ apt-get install linux-headers-2.6.24-19-generic
                  linux-image-2.6.24-19-generic
                  linux-restricted-modules-2.6.24-19-generic
                  linux-ubuntu-modules-2.6.24-19-generic
$ apt-get remove  linux-headers-2.6.24-17-generic
                  linux-headers-2.6.24-18-generic
                  linux-image-2.6.24-17-generic
                  linux-image-2.6.24-18-generic
                  linux-restricted-modules-2.6.24-17-generic
                  linux-restricted-modules-2.6.24-18-generic
                  linux-ubuntu-modules-2.6.24-17-generic
                  linux-ubuntu-modules-2.6.24-18-generic
```

I did this on both computers.  I then reinstalled the Nvidia drivers for each, checked the */etc/X11/xorg.conf* and */boot/grub/menu.lst* on each of them, and rebooted.

They both work fine!

---

### Post by bkline on 2008-06-06
> **ohiomoto said:**
> What do the headers do anyway?  Are they included in the linux-image

The headers are C language files (text, not binary) which contain declarations and definitions which tell the compiler what the meaning of names is in the main C source code.  For example, "#define BUFFER_OFFSET 50" in a header file will cause the C pre-processor to substitute "50" where it finds "BUFFER_OFFSET" (I'm simplifying - it doesn't do this everywhere) before it compiles the program into binary executables.  Another example would be a "struct" definition which tells the compiler how certain blocks of named memory will be laid out.  They're not so much "included" in the linux-image binary as they are used to build that binary, which is the executable code for the core of the operating system, taking care of all of the low-level stuff (with the help of drivers).  If a program which needs to communicate with the kernel somehow uses the wrong header files when it's built, then its picture of how memory blocks are laid out could very well be different from that used by the kernel, and it's easy to see how disaster could result, particularly if the program is a driver, running with elevated privileges.  So perhaps something along these lines is happening here.

Sorry if that's more than you really wanted to know.  Trust me - I'm over-simplifying the explanation.  For a peek at a representative header file, try ```
less /usr/src/linux-headers-2.6.24-17-generic/include/linux/pci.h
```  I was surprised to see so few differences in the output from ```
diff -r /usr/src/linux-headers-2.6.24-17-generic /usr/src/linux-headers-2.6.24-18-generic
``` given all the havoc we're dealing with.  I do see a couple of odd values for CONFIG_UNAME_RELEASE (why would -17 have "2.6.24-15-server" and -18 have "2.6.15.7"?).

Cheers,
Bob

---

### Post by ohiomoto on 2008-06-06
> **Dale61 said:**
> If it helps, I have the following installed:
linux-headers 2.6.24-16 + generic
linux-headers 2.6.24-17 + generic
linux-headers 2.6.24-18 + generic
linux-headers-generic
linux-image-2.4.24-15-generic
linux-image-2.4.24-16-generic
linux-image-2.4.24-17-generic
linux-image-2.4.24-18-generic
linux-image-686
linux-image-generic

as well as the restricted modules for same, and ubuntu modules.

My system is running without a problem, and all updates go smoothly and flawlessly.

Of the above, can any be removed, or is it best to retain them?  Hard drive space is not a problem at this stage as I have 68GB remaining (out of 82).

I reinstalled the headers and no matter what combination of -17 & -18 headers I use, the problems come back.  Basically, I can use either kernel by itself its headers or both kernels without any headers.  Do I need the headers??

What's up with the dummy update kernels?  I see you have an image of 686.  What does that doe for you?

---

### Post by jtrindle on 2008-06-06
The headers themselves shouldn't alter the way the system runs, as far as I know they are just used for compilation from source.

I wonder if there is a problem with the package cache?  And installing or removing packages gets around the problem (for a while, until other packages are installed)?  This might cause Update Manager to glitch.

You can clean out your package cache and history under

Synaptic->Settings->Preferences->Files

---

### Post by ohiomoto on 2008-06-06
> **bkline said:**
> 
Sorry if that's more than you really wanted to know.  Trust me - I'm over-simplifying the explanation. 
Thanks.  I sort of understand what your saying, kind of like variables made available to the system.  (I've really over-simplified it now.)

I tried running the code, but I forgot that I don't have headers!

I'm thinking I might be better off taking a chance using one kernel with headers than using both without headers.

---

### Post by ohiomoto on 2008-06-06
> **jtrindle said:**
> I wonder if there is a problem with the package cache?  And installing or removing packages gets around the problem (for a while, until other packages are installed)?  This might cause Update Manager to glitch.

You can clean out your package cache and history under

Synaptic->Settings->Preferences->FilesThat makes sense.  I'll try it and see if I can get those headers back in there.

Thanks!

---

### Post by ohiomoto on 2008-06-06
> **jtrindle said:**
> 
I wonder if there is a problem with the package cache?  And installing or removing packages gets around the problem (for a while, until other packages are installed)?  This might cause Update Manager to glitch.

You can clean out your package cache and history under

Synaptic->Settings->Preferences->FilesBINGO!!!!!!!!

Did that and then put both sets of headers back in.  Both kernels appear to be working properly.  I guess I CAN have my cake and eat it too!

Thanks to everyone who helped out.  All of that hard work trying to pinpoint the issue was worth it now that someone found the solution.  


I hope this helps others sort this issue out.  More importantly, I hope I'm not hosed again when the next update shows up! lol

THANKS AGAIN!

---

### Post by Dale61 on 2008-06-06
> **ohiomoto said:**
> I reinstalled the headers and no matter what combination of -17 & -18 headers I use, the problems come back.  Basically, I can use either kernel by itself its headers or both kernels without any headers.  Do I need the headers??

What's up with the dummy update kernels?  I see you have an image of 686.  What does that doe for you?

I don't even know if the 686 image is even needed now, but it was needed back when I ran 6.06 with a dual core cpu.

---

### Post by bkline on 2008-06-06
> **Dale61 said:**
> I don't even know if the 686 image is even needed now, ....

Here's what apt-cache has to say about the linux*-686 packages: ```
Upgrade dummy package. Can be removed
```

---

### Post by Dale61 on 2008-06-06
Yeah bk, it also states that in the synaptic description, but as my pc is working at 100%, 100% of the time, I'm not going to start removing anything related to kernels just at this time.

---

### Post by bkline on 2008-06-06
> **Dale61 said:**
> Yeah bk, it also states that in the synaptic description, but as my pc is working at 100%, 100% of the time, I'm not going to start removing anything related to kernels just at this time.

Sure, wasn't recommending it, just responding to what I (possibly in error) took to be the implied question in your "I don't even know if the 686 image is even needed now" since I had remembered seeing that annotation earlier.

---

### Post by Dale61 on 2008-06-06
Mate, no problems.

In theory, I could remove the 686 image, along with the -15, -16 and -17 related packages, but as my pc is running basically 24/7, I really can't afford the downtime if my system implodes.

---

### Post by bkline on 2008-06-07
> **ohiomoto said:**
> BINGO!!!!!!!!

Did that and then put both sets of headers back in.  Both kernels appear to be working properly.

Kudos for your persistence and willingness to keep experimenting to track this down.  Well done!

Bob

---

### Post by mtantawy on 2008-06-07
well, i removed totally everything related to kernels and headers ending with 16&17, i restarted my laptop, i felt it is a little better, but:(
the update manager still not working .
i cant access internet""till now-i am on VISTA""
rhythmbox still no response neither amarok does and still recieve error that sound device is busy

so now, what should i do?how can i install back the kernel 2.6.24-17 or 16 without update manager???

i have only choice of kernel 2.6.24.18 like what u said but still stuff r not the way they used to at all :S

also please how do i differentiate between updates that r final and ready and ones that r like BETA??
i used to see 2 keywords GENERIC & META, what does each mean?

sry for the too many questions but i am very beginner and i am interested much in ubuntu & linux in general....

Thanks in advance
Mahmoud Tantawy

---

### Post by Dale61 on 2008-06-07
The last time I updated using update manager was when I went from 6.06 to 8.04.  Since then, all my updating gets done via Synaptic.

All updates this way have gone accordingly, and without a hitch.

---

### Post by ohiomoto on 2008-06-07
> **mtantawy said:**
> well, i removed totally everything related to kernels and headers ending with 16&17, i restarted my laptop, i felt it is a little better, but:(
the update manager still not working ....
Mahmoud Tantawy

Mahmound,

I think this was the key to clearing up my problems:
> **jtrindle said:**
> The headers themselves shouldn't alter the way the system runs, as far as I know they are just used for compilation from source.

I wonder if there is a problem with the package cache?  And installing or removing packages gets around the problem (for a while, until other packages are installed)?  This might cause Update Manager to glitch.

You can clean out your package cache and history under

Synaptic->Settings->Preferences->Files

So try this before you go through all of the adding/removing packages:
1. Clean out the package cache and history in Synaptic by going to "Synaptic->Settings->Preferences->Files".  Hopefully this will make sure you avoid any issues.

2.  Go down the list and mark the following packages for installation or re-installation:```
linux-image-2.6.22-18-generic
linux-headers-2.6.22-18-generic
liux-restricted-modules-2.6.22-18-generic
linux-ubuntu-modules-2.6.22-18-generic
```

---

### Post by Dale61 on 2008-06-07
> **ohiomoto said:**
> 

2.  Go down the list and mark the following packages for installation or re-installation:```
linux-image-2.6.22-18-generic
linux-headers-2.6.22-18-generic
liux-restricted-modules-2.6.22-18-generic
linux-ubuntu-modules-2.6.22-18-generic
```

Shouldn't it be 2.6.24-18?

---

### Post by mtantawy on 2008-06-07
> **Dale61 said:**
> Shouldn't it be 2.6.24-18?
yeah i think so it should be 24, am gonna make it 24 and c what will happen, just after an hour or so

---

### Post by mtantawy on 2008-06-07
:mad::mad::mad::mad::mad:
slow progress, the power button is working and the update manager is back
i am doing an update that doesnt include any kernels"i wish"
but still the rhythmbox not responding to a double click on the music file even in its library
the internet is back before fixing

so, what does this mean and what should i do again?
and why the old kernels caused such problems or it is a conflict between the old ones and the new one??

---

### Post by ohiomoto on 2008-06-07
> **Dale61 said:**
> Shouldn't it be 2.6.24-18?Yes.  Sorry about that.

I also have the corresponding -17 packages in place.  Both kernels are running great and I've made it through one minor system update without any problems.

---

### Post by ohiomoto on 2008-06-07
> **mtantawy said:**
> 
so, what does this mean and what should i do again?
and why the old kernels caused such problems or it is a conflict between the old ones and the new one??Not sure what to tell you.  Maybe try adding the -17 packages and see if you have better luck.

---

### Post by mtantawy on 2008-06-08
> **ohiomoto said:**
> Not sure what to tell you.  Maybe try adding the -17 packages and see if you have better luck.
before you tell me, i've done that last night, but i removed -18 and installed -17 with all its dependencies "to make sure"
after a 50 MB download or so, i rebooted, and it started okay with no errors but it stop just after writing my username and password :'(
think i messed it up totally this time...

i think now the only way is a new installation , but so, what kernels should i update to ???or stay on the -16???

note that i install using Wubi because "as you see" am still tryin ubuntu out...

so any suggestions???
i really really would like to understand why all this is happening?is it hardware issue or what!!!!

Thanks so much for providing help n being patient

Mahmoud Tantawy

---

### Post by mtantawy on 2008-06-08
> **mtantawy said:**
> before you tell me, i've done that last night, but i removed -18 and installed -17 with all its dependencies "to make sure"
after a 50 MB download or so, i rebooted, and it started okay with no errors but it stop just after writing my username and password :'(
think i messed it up totally this time...

i think now the only way is a new installation , but so, what kernels should i update to ???or stay on the -16???

note that i install using Wubi because "as you see" am still tryin ubuntu out...

so any suggestions???
i really really would like to understand why all this is happening?is it hardware issue or what!!!!

Thanks so much for providing help n being patient

Mahmoud Tantawy
hey, anybody here!!!!

---

### Post by bkline on 2008-06-08
> **mtantawy said:**
> hey, anybody here!!!!

Well, patience works in both directions. :)

The things that make it difficult for those of us who are not familiar with the internals of the kernel and the package management system to know what advice to give you are [LIST=1]
[*]we don't really understand what is causing the failures; and
[*]different users posting to this thread have solved the problems with completely different actions
[/LIST]

The one suggestion which was made (by ohiomotu, the OP) that it's not completely clear to me you've tried is clearing out the package manager's cache (see instructions earlier in the thread).  If you haven't tried that, please give it a shot.  If you have tried, and it didn't work, then indeed reinstalling from scratch may be one of your few remaining options.   At that point, in response to your question about which kernel(s) to install: if I were in your shoes, I'd give serious consideration to the approach of holding off on any kernel updates beyond the version that ships with 8.04 until -19 is in the default channels (keeping my firewall and physical security as tight as possible in case I'm missing some critical security patches by doing this).  You might also try and find the bug reports related to these failures and vote for them in a feeble attempt to try and get the attention of the maintainers.  Unless/until they take pity on us and grace us with some insight into what's wrong with the latest kernel and/or the package manger we're all just floundering half-blind.

Sorry I can't provide you with a guaranteed solution.  Good luck!

---

### Post by mtantawy on 2008-06-08
> **bkline said:**
> Well, patience works in both directions. :)

The things that make it difficult for those of us who are not familiar with the internals of the kernel and the package management system to know what advice to give you are [LIST=1]
[*]we don't really understand what is causing the failures; and
[*]different users posting to this thread have solved the problems with completely different actions
[/LIST]

The one suggestion which was made (by ohiomotu, the OP) that it's not completely clear to me you've tried is clearing out the package manager's cache (see instructions earlier in the thread).  If you haven't tried that, please give it a shot.  If you have tried, and it didn't work, then indeed reinstalling from scratch may be one of your few remaining options.   At that point, in response to your question about which kernel(s) to install: if I were in your shoes, I'd give serious consideration to the approach of holding off on any kernel updates beyond the version that ships with 8.04 until -19 is in the default channels (keeping my firewall and physical security as tight as possible in case I'm missing some critical security patches by doing this).  You might also try and find the bug reports related to these failures and vote for them in a feeble attempt to try and get the attention of the maintainers.  Unless/until they take pity on us and grace us with some insight into what's wrong with the latest kernel and/or the package manger we're all just floundering half-blind.

Sorry I can't provide you with a guaranteed solution.  Good luck!
Thanks alot, i appreciate u all doing ur best to provide solutions, i really do, and forgive me for asking many questions again n again but i just love to learn how to fix and what was wrong from the beginning...

i cant log into the system anymore, i got error that some files were missing so i'll consider new clean install but with wubi also till i finish my exams duration n be ready to explore deeply Ubuntu"ofcourse am gonna count on u all to help me :D "...

i wont install any update till as u said the kernel -19 is out...

considering send the error log, i cant in the moment cause as i said am in the middle of exams and kinda busy...

Thanks all really

Mahmoud Tantawy

---

### Post by Sub101 on 2008-06-08
Does the -19 kernel work any better for you?

---

### Post by bkline on 2008-06-08
> **Sub101 said:**
> Does the -19 kernel work any better for you?

Don't know.  It doesn't show up in APT's list of available packages for 8.04.  I look forward to trying when it does.

---

### Post by Sub101 on 2008-06-08
mine upgraded upon typing either

```
sudo apt-get update
or
sudo apt-get upgrade
```

cant remember which I do them at the same time normally.

---

### Post by bapoumba on 2008-06-08
> **Sub101 said:**
> mine upgraded upon typing either

```
sudo apt-get update
or
sudo apt-get upgrade
```

cant remember which I do them at the same time normally.

Run them back to back:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
update : reads the sources.list file
dist-upgrade : upgrades and checks for dependencies more carefully than a regular upgrade.

---

### Post by bkline on 2008-06-08
Well, I thought I'd be a good citizen, following ohiomotu's brave example, and see if I could provide some additional data points as ammunition for hunting down the cause(s) and hopefully solution(s) for the failures.  As you may recall from earlier in the thread, I reported that I was able to solve the problem by falling back to 2.6.24-17, and indeed the machine in question had been running flawlessly with heavy usage for days using that kernel, without the need for any of the other measures mentioned in this thread.

At any rate, I decided that I would (a) confirm that -18 was still broken and that -17 was still working properly, and (b) see if following the instructions earlier in the thread for clearing out the package manager's cache would make -18 run successfully again.  So I rebooted into -18, and confirmed that in fact before too long the machine was locked up tighter than a drum.  Rebooted back into -17 and things were working fine again, so seemingly (a) was taken care of.  Then I followed the instructions for clearing out the package manager's cache and rebooted into -18.  Machine froze after about 60 seconds.  So back to -17, but that froze now as well.  I've tried quite a few things since then, including removing and reinstalling -18, as well as removing the older kernels and their headers and modules, but the end result is dismal.  I now have no working kernel on the system. :(

I filed a [bug report]("https://bugs.launchpad.net/bugs/237612") a few days ago in launchpad, but unfortunately there doesn't seem to be any way for ordinary Ubuntu users to influence the prioritization of the bug reports to make sure the real show stoppers get noticed by the package maintainers, so it's just been floating out there in the void pretty much unnoticed.

A sad day for Ubuntu.

---

### Post by mtantawy on 2008-06-08
am just so so sorry to hear so about yr system
seems that u reached the same result as me :(

now i installed a new clean one using Wubi
but i forgot what settings should i use while installing and setting the partitions

so plz help me, i have 3 choice
1)guided-use whole disk
2)guided-use largest continuous space "gives error, but i think this is because my hard disk is loaded to the rim"
3)manual

so best choice for beginner is the first but it give me warning that sda 1&5 will be formatted and data will be lost..
what should i do?i need all my data and i remember that my last install didnt harm any partitions"even the partition it was installed into side by side with win XP", but i just cant remember what i've done in that last install

wishing u good luck in yr install

EDIT::i forgot to say that my suspend/hibernate r both back in action thanks to kernel-16 .....
so kernel -17 and -18 case problems to suspend/hibernate which was known to be problem with ATI hardware...

Mahmoud Tantawy

---

### Post by ohiomoto on 2008-06-08
> **bkline said:**
> A sad day for Ubuntu.Bummer! I am really sorry about your system.  You didn't have to do that.  I was the one who didn't care if I had to do a new install, not you.

It's strange that so many people are having so much trouble, yet what seems to work for one, doesn't always work for another.  I mean I was able to add and subtract Kernels and headers at will and my system would always respond in as "expected" almost as if I could turn the problems on and off.  The jtwiddle offers and idea and now everything works perfectly.  You do the same thing and your system gets hosed.  Yet others get the update without issue.  Strange....

---

### Post by ohiomoto on 2008-06-08
> **mtantawy said:**
> 

so plz help me, i have 3 choice
1)guided-use whole disk
2)guided-use largest continuous space "gives error, but i think this is because my hard disk is loaded to the rim"
3)manual
If you want to dual boot XP choose #3.  Good luck.

---

### Post by mtantawy on 2008-06-08
> **ohiomoto said:**
> If you want to dual boot XP choose #3.  Good luck.
if i choose 3 i must format a partition to free it for ubuntu, moreover this option sometime doesnt work and return me to the choices page

i have 3.5 GB free after subtracting the minimum needed 4 GB from that partition that hold XP
btw, i am installing Wubi from Vista which is on another partition"all on one hard disk"

i explored some tutorials for instaling, all suggested an option which doesnt exist in my installation"how?",,this option is to resize the windows partition or smthin like that and installing ubuntu side by side, which seems to be the correct choice"i dont have it ^o) "

---

### Post by Dale61 on 2008-06-08
> **ohiomoto said:**
> Bummer! I am really sorry about your system.  You didn't have to do that.  I was the one who didn't care if I had to do a new install, not you.

**It's strange that so many people are having so much trouble**, yet what seems to work for one, doesn't always work for another.  I mean I was able to add and subtract Kernels and headers at will and my system would always respond in as "expected" almost as if I could turn the problems on and off.  The jtwiddle offers and idea and now everything works perfectly.  You do the same thing and your system gets hosed.  Yet others get the update without issue.  Strange....

So many people?  At last count it was only three in this thread. :)

I've gone in to synaptic and removed all traces of any kernel prior to -17, and all is still sweet.

GRUB only shows -18 when I fire up, so that is what I boot into, and I don't have a problem.  In start-up manager, I have defaulted to show 1 kernel in GRUB, so I don't ever see any other than the most current kernel.

When I did my upgrade from 6.06, I did so via the update manager (which took 100 hours), and any new update gets done via synaptic.

To help clear up any lurking files that may be conflicting, try this in a terminal:
```
sudo aptitude autoclean
```

When I first did this, it cleaned up about 50MB of space.  I now do this after every update.

---

### Post by badfish591 on 2008-06-08
i can no longer get my patched rtl8187b driver for my wireless to work in the -18 kernal. still using -16 here

---

### Post by bkline on 2008-06-08
> **Dale61 said:**
> So many people?  At last count it was only three in this thread. :)

Tim has also been reading (and responding to) some of the other threads in which users are reporting problems with this kernel.  Just out of curiosity, how many unusable systems would it take before we could regard this as a real problem? :-)

---

### Post by ohiomoto on 2008-06-08
> **bkline said:**
> Just out of curiosity, how many unusable systems would it take before we could regard this as a real problem? :-)That depends who's system you're talking about.  If it's my computer, then it's a problem! lol

---

### Post by nsramkishen on 2008-06-09
@ohiomoto

I have the same 16-works-but-17-and-18-don't-work-well issue. I am new to Ubuntu (have done a bit of Unix long ago) and this thread serves as a try-it-yourself lab. I will try all the options discussed to bring -18 to life in my machine. I swear:neutral:.

---

### Post by bkline on 2008-06-09
> **nsramkishen said:**
> @ohiomoto

I have the same 16-works-but-17-and-18-don't-work-well issue. I am new to Ubuntu (have done a bit of Unix long ago) and this thread serves as a try-it-yourself lab. I will try all the options discussed to bring -18 to life in my machine. I swear:neutral:.

Be warned that this might result in **none** of the kernels on your machine being usable (that's what happened to me).

---

### Post by mtantawy on 2008-06-09
> **mtantawy said:**
> if i choose 3 i must format a partition to free it for ubuntu, moreover this option sometime doesnt work and return me to the choices page

i have 3.5 GB free after subtracting the minimum needed 4 GB from that partition that hold XP
btw, i am installing Wubi from Vista which is on another partition"all on one hard disk"

i explored some tutorials for instaling, all suggested an option which doesnt exist in my installation"how?",,this option is to resize the windows partition or smthin like that and installing ubuntu side by side, which seems to be the correct choice"i dont have it ^o) "

BKLINE, can you help me with this or anyone??

---

### Post by bkline on 2008-06-09
> **mtantawy said:**
> BKLINE, can you help me with this or anyone??

Sorry, I'm not familiar with Wubi.  Besides, I'm one of the users with a broken system, remember?  Probably want to get advice from someone having better luck ducking the bugs. :-)

---

### Post by mtantawy on 2008-06-09
> **bkline said:**
> Sorry, I'm not familiar with Wubi.  Besides, I'm one of the users with a broken system, remember?  Probably want to get advice from someone having better luck ducking the bugs. :-)
hehe :D
thanks anyway
and wish u luck again, just plz iff u reached a solution or better a explanation post it here in this dear THREAD....

gonna give it a try just after my exams 19/6

Mahmoud Tantawy

---

### Post by hoboken on 2008-06-09
Hey guys, I'm having trouble understanding what all this kernel stuff is about. I have 2.6.24-18, 2.6.22-14 and 2.6.20-16 in GRUB and the only difference between 18 and 14 is that in 14, compiz runs slightly smoother. So I'm using that one right now.

What are possible issues with running an outdated kernel? Should I update to 19?

Cheers and sorry for the slight thread hijack!

---

### Post by ohiomoto on 2008-06-10
If you have a kernel that runs well, then use it.  "If it ain't broke, don't fix it."   

My -18 "broke" my system when I first got the update.  First time I ever had an issue with Ubuntu and I've run it on six different Laptops over the past year.  Now that my -18 kernel is running as it should, I'm very pleased with it.  I've had no update issues, compiz and wireless are working fine and everything is much faster ( including the updated Firefox 3).

---

### Post by ohiomoto on 2008-06-10
:confused:

Broke again...both kernels.

Tried to download VMware Workstation.  Wouldn't save the file correctly and had to force quit the download manager.  My internet connection was slow so I rebooted, but it turned out that all my machines were slow...problems with the ISP.  Anyway upon start up the exact same set of problems are back except my wireless is up and running as normal.  

Go figure????  (Shaking my head.)

---

### Post by bkline on 2008-06-10
I turned on the 'proposed' repo and pulled down -19, which didn't solve the problems, so I scrubbed the disk and did a fresh install of 8.04.  I plan to stick with the kernel I got with that installation until the problems with the later kernels are diagnosed and resolved.  As they say, YMMV.

Cheers,
Bob

---

### Post by ohiomoto on 2008-06-10
Okay, I gave -19 a shot...didn't work.

I took out all -17 packages...didn't work.

I took out all -18 packages leaving me with only -19...didn't work.

I took out all of the -19 header packages...BINGO...back to normal...again.

Once again, it's pointing to the header packages. I'm going to try clearing the cash and see if I can put the headers back in.  Then I'll see if I'm able to set up VMwear.  

Even if that works, I think there is some conflict that I haven't resolved.  I can't see putting much more into this release.  I really need to set up some stuff so I can start working on a project and I can't afford to be hosed once I get started.  Who knows, I might even be in WINDOWS again for a while...okay, probably ubuntu 7.10 or maybe I'll give 64-bit 8.04 another go.

---

### Post by mtantawy on 2008-06-10
> **ohiomoto said:**
> Okay, I gave -19 a shot...didn't work.

I took out all -17 packages...didn't work.

I took out all -18 packages leaving me with only -19...didn't work.

I took out all of the -19 header packages...BINGO...back to normal...again.

Once again, it's pointing to the header packages. I'm going to try clearing the cash and see if I can put the headers back in.  Then I'll see if I'm able to set up VMwear.  

Even if that works, I think there is some conflict that I haven't resolved.  I can't see putting much more into this release.  I really need to set up some stuff so I can start working on a project and I can't afford to be hosed once I get started.  Who knows, I might even be in WINDOWS again for a while...okay, probably ubuntu 7.10 or maybe I'll give 64-bit 8.04 another go.
so u suggest that one with fresh install should update directly to kernel -19 without the headers??

wish this be the solution....

---

### Post by mtantawy on 2008-06-10
> **ohiomoto said:**
> Okay, I gave -19 a shot...didn't work.

I took out all -17 packages...didn't work.

I took out all -18 packages leaving me with only -19...didn't work.

I took out all of the -19 header packages...BINGO...back to normal...again.

Once again, it's pointing to the header packages. I'm going to try clearing the cash and see if I can put the headers back in.  Then I'll see if I'm able to set up VMwear.  

Even if that works, I think there is some conflict that I haven't resolved.  I can't see putting much more into this release.  I really need to set up some stuff so I can start working on a project and I can't afford to be hosed once I get started.  Who knows, I might even be in WINDOWS again for a while...okay, probably ubuntu 7.10 or maybe I'll give 64-bit 8.04 another go.
so u suggest that one with fresh install should update directly to kernel -19 without the headers??

wish this be the solution....

---

### Post by ohiomoto on 2008-06-10
You're asking the wrong guy!  lol  Maybe a fresh install without any updates, but that's not exactly what I had in mind.

Anyway I have the headers back in and it still works.   Now I'll wait for it to break again. We'll see what VMware has in store for me. :(

---

### Post by mtantawy on 2008-06-10
see the next post, ignore this one it was a repeat....

---

### Post by mtantawy on 2008-06-10
so you applied the headers that broke the system before but till now running okay!!!strange

may be its the sequence of the update process thats causing all those failures and strange breaks.

i think we should apply the kernel alone first then install and restart then apply its headers...

Haven't you noticed that??

---

### Post by ohiomoto on 2008-06-10
Now it gets even stranger!

I went to download a 200mb VMware .tar and it would finish the download saying I didn't have enough room.  It did this earlier but I didn't think to look into it.

> 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8              20G   19G  169M 100% /
varrun               1013M  104K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M   60K 1013M   1% /dev
devshm               1013M   12K 1013M   1% /dev/shm
lrm                  1013M   38M  976M   4% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       20G   19G  169M 100% /home/ohiomoto/.gvfs
My file system used to be less than 10GB and now it's almost 100% full.  All that I've put on the system is couple of IDE's, a JDK and ubuntu updates.  

Not sure what to make of this.  I'm pretty close to starting over.  Any ideas???

---

### Post by Dale61 on 2008-06-10
> **ohiomoto said:**
> :confused:

Broke again...both kernels.

**Tried to download VMware Workstation.  Wouldn't save the file correctly and had to force quit the download manager.**  My internet connection was slow so I rebooted, but it turned out that all my machines were slow...problems with the ISP.  Anyway upon start up the exact same set of problems are back except my wireless is up and running as normal.  

Go figure????  (Shaking my head.)

If it were me, I would be concentrating on getting my basic system up and running before trying to download other programs.

To each their own, I suppose,

---

### Post by ohiomoto on 2008-06-10
Dale61, 

It was up and running perfectly (for a few days) before I started adding some of the tools MY basic system is going to need.  That is when it broke again...or should I say I found out that it was never "fixed" to begin with.  So it's reaching a the point where I'll just need to boot XP and that will be my main system and test linux in VMware until I get my projects done.  I was hoping to avoid that.

---

### Post by mridkash on 2008-06-11
The disk space issue, 
try clearing apt cache, after downloading updates, it stores packages there.
```
rm /var/cache/apt/archives/*
```
or you can manually browse to folder and delete all files permanently.
Or try clearing the thumbnail cache, if you have lots of photos, videos stuff.
Home Folder > press Ctrl-H > find .thumbnails > delete all inside it
I think this'll save you some space.

---

### Post by Cresho on 2008-06-11
> **bapoumba said:**
> i Usually Keep The Previous Working Kernel, Just In Case :)

Dido!

---

### Post by mtantawy on 2008-06-11
> **ohiomoto said:**
> Now it gets even stranger!

I went to download a 200mb VMware .tar and it would finish the download saying I didn't have enough room.  It did this earlier but I didn't think to look into it.

My file system used to be less than 10GB and now it's almost 100% full.  All that I've put on the system is couple of IDE's, a JDK and ubuntu updates.  

Not sure what to make of this.  I'm pretty close to starting over.  Any ideas???
smthing like this keep happening to me too, always telling me no disk space even to save a small text file, even after deleting about 20 MB of data from my desktop"ofcourse from the trash too"

second thing, how do u get those details about the disk usage??
i cant find a way to tell me how much is left or how much is used because simply the filesystem doesnt show this info in its properties...

---

### Post by ohiomoto on 2008-06-11
> **mridkash said:**
> The disk space issue, 
try clearing apt cache, after downloading updates, it stores packages there.
```
rm /var/cache/apt/archives/*
```Thanks,  

But I did that plus I had no data files stored on the system.  At the time I only had one kernel installed and I even removed the few programs I had added.  I was still at 20GB something bloated my system up.  I did a fresh install of 6.22.24-16, added all updates (including 22.24.6-18 ) and compiz last night.  Now I have -16 & -18 and the same software I had before My system is at 2.6GB running great so far.

---

### Post by ohiomoto on 2008-06-11
Still running strong on the new install and updates.  Have VMware running an a XP image with Flex Builder.  Still have some IDEs and Java stuff to put on, but so far everything seems to be fine.

I wonder if it's possible -17 updates or a Java package might have done some damage between my initial -16 install and the recent -18 updates?

I'll post if I run into any more problems.  I'm still interested to hear how others are making out and any other ideas as to what could be going on.

Thanks.

BTW, My system has most of what I need and it's still less than 10GB.  There is no way my broken system should have hit 20GB...something was not right.

---

### Post by bkline on 2008-06-12
> **mtantawy said:**
> second thing, how do u get those details about the disk usage??
i cant find a way to tell me how much is left or how much is used because simply the filesystem doesnt show this info in its properties...

The command [df]("http://linux.die.net/man/1/df") will do that for you.

---

### Post by lhc_surfer on 2008-06-14
> **ohiomoto said:**
> UPDATED---HOSED AGAIN!!!!!!
see page 8


Installed available updates this morning and my system is hosed.

1.  System won't shut down properly.  After hitting the "power" icon the system hangs on a blank desktop.[LIST]
[/LIST]  I have to power down the computer shutdown.

2.  I have to get online "manually".  Once I get online networking returns to normal.

3.  Firefox--lost all bookmarks and the ability to use bookmarks.  But history is still available.

4.  Firefox-- Won't browse "Back" or "Forward". 

Tried booting to kernel 2.6.24.-17 with the same results.

Anyone else run into these problems?

Best way to resolve the issue?

Reinstall 8.04 (or maybe 7.10 would be a better idea:( )?


I've encountered the exactly the same problem, so I removed old kernels (or that's what I thought I'd done.. I'm not an expert). It worked fine for 2 or 3 sessions, than the same problem appeared again, as if nothing had been done.
Does anyone know another solution? 
Could you be more specific when you talk about removing kernels? I'm not sure I did the right thing.
Thank you!

---

### Post by ohiomoto on 2008-06-14
Sorry lhc.  I never did figure out what was going on.  Seems like some residual problems that I couldn't get cleaned up.  I ended up with a fresh install.  Everything has been working perfectly since then.  running XP on VM Workstation while using Firefox 3 and streaming music in ubuntu.  I couldn't be happier with the way everything is working right now.
> **ohiomoto said:**
> I did a fresh install of 6.22.24-16, added all updates (including 22.24.6-18 ) and compiz last night.  Now I have -16 & -18 and the same software I had before My system is at 2.6GB running great so far.

---

### Post by NullHead on 2008-06-17
The update went with out notice on all three of my 8.04 installs :confused: I've even installed ubuntu server recently and it didn't have a problem either.

---

### Post by bkline on 2008-06-17
> **NullHead said:**
> The update went with out notice on all three of my 8.04 installs :confused: I've even installed ubuntu server recently and it didn't have a problem either.

I'm sure there are at least a thousand Ubuntu machines for which the new kernel update presented no problem for every one which broke.  I myself have four other Ubuntu systems in the former category, and only one which was clobbered.  Perhaps the new kernel didn't like some hardware component unique (among my machines) on the broken system.  Maybe a combination of components that violated some assumption deep inside the kernel.  Or it might have been that this machine happened to have a software package (or combination of packages) which didn't play well with the new kernel.  Might not have been the kernel at all: the update containing the -18 kernel had other package upgrades in it, and it's possible that one of them wasn't ready for prime time.  I had hoped that one of the Ubuntu/Linux gurus would have provided some guidance for turning on some extra logging or dumps or traces or whatever you need to do in order to diagnose the cause of the failures reported here, but it's not terribly surprising if it doesn't turn out that way with the luck of the draw in threads on an open forum.  It was more disappointing to have gotten no such guidance in response to the bug report I filed.

Eventually I just gave up, cut my losses, and replaced the system.  I guess Ubuntu has gotten so popular that the maintainers see an occasional busted system here or there as an acceptable level of collateral damage.

Cheers,
Bob

---

### Post by shareme on 2008-06-17
Mine would not take the 2.6.24.19 kernel upgrade ie would not boot up properly..


My temp fix was to use esc command at boot up menu and choose the 2.6.24.18 kernel to boot up  into

---

### Post by ohiomoto on 2008-06-18
My -19 update installed without any issues, But I have to admit I was afraid to take them!

I'm with bkline, there must have been somthing "damaged" on my system prior to my -18 update (or something that came with it).  I now have -16, -18, and -19 on my system and they all work fine.

---

### Post by mtantawy on 2008-06-18
> **bkline said:**
> I'm sure there are at least a thousand Ubuntu machines for which the new kernel update presented no problem for every one which broke.  I myself have four other Ubuntu systems in the former category, and only one which was clobbered.  Perhaps the new kernel didn't like some hardware component unique (among my machines) on the broken system.  Maybe a combination of components that violated some assumption deep inside the kernel.  Or it might have been that this machine happened to have a software package (or combination of packages) which didn't play well with the new kernel.  Might not have been the kernel at all: the update containing the -18 kernel had other package upgrades in it, and it's possible that one of them wasn't ready for prime time.  I had hoped that one of the Ubuntu/Linux gurus would have provided some guidance for turning on some extra logging or dumps or traces or whatever you need to do in order to diagnose the cause of the failures reported here, but it's not terribly surprising if it doesn't turn out that way with the luck of the draw in threads on an open forum.  It was more disappointing to have gotten no such guidance in response to the bug report I filed.

Eventually I just gave up, cut my losses, and replaced the system.  I guess Ubuntu has gotten so popular that the maintainers see an occasional busted system here or there as an acceptable level of collateral damage.

Cheers,
Bob
i totally agree with you , in both points

that the maintainers dont act as they should&that it might a hardware issue or software combination error

also i wonder why dont i see any replies from those involved in making Ubuntu or at least why isn't there a team to help in this forum???
if u've noticed, we are all guessing and trying to figure out whats going on, very little are the experienced...

i wish experienced people and developers join us in this forum, especially that this is an official one not a forum owned by sm guy who like Ubuntu, am i wrong in my wish!!!!!

cheers,
Mahmoud Tantawy

---

### Post by Dale61 on 2008-06-18
I just upgraded to -19, and it was smooth and sweet.

In Synaptic, the updates are listed in alphabetical order, but as I used the Update Manager this time, I made a note of what order the updates were downloaded / installed.

As per Update Manager:

linux-image-2.4.24-19-generic
linux-ubuntu-modules-2.6.24-19-generic
linux-headers-2.6.24-19
linux-headers-2.6.24-19-generic
linux-headers-generic
linux-image-generic
linux-libc-dev
linux-restricted-modules-common
linux-restricted-modules-2.6.24-19-generic
linux-restricted-modules-generic

So, any problems may be related to the order of download / installation, rather than the kernel itself.

---


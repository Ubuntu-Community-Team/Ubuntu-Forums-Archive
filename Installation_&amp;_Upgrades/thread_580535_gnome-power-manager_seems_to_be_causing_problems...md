---
title: "gnome-power-manager seems to be causing problems..."
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by ruggersway on 2007-10-18
Can gnome-power-manager be totally disabled?  If so, how?

Now - the explanation:

I just installed the new 7.10 today on my laptop, I'd been running 7.04 for some time with no problems.  Upon installing 7.10 today, everything was great...until I got home.  

When attempting to log in while on battery power the desktop would start to load - then everything goes black.  I can't ctrl-alt to a terminal or anything.  All I can do is power down.  

So I plugged in and boot into a terminal to back up my data.  After backing up data, I decided to try logging in again - it worked.  :confused:

So I unplug the power cord, black screen immediately - plugging back in returns the desktop and I see a message about being on battery power so I kill gnome-power-manager and unplug again.  Now everything is fine.  I proceeded to install kpowersave, I was running it in 7.04 because I like the ease of adjusting the cpu.

I removed gnome-power-manager from the session in hopes of disabling it, which doesn't work.  Fortunately, with kpowersave also running things still work.  I don't know if anyone else has experienced this and perhaps found a solution?  

Should this be filed as a bug?  I know there were changes made to the power management in this release, they don't seem to be having the desired effect on my laptop. 

Any ideas or suggestions would be appreciated.  The desktop takes considerably longer to load than on 7.04 too, I'm assuming it has to do with this as well.

I'm wasn't sure where to put this - move me if I'm in the wrong place.

-rugger

---

### Post by icechen1 on 2007-10-19
It is happening to me too,however i managed to fix it by setting the light brightness to max.Even if the power is on and i try to set the light brightness,the screen just tuns black(but you can still see a little).
I believe this is a bug and it didn't happened in feisty,only in Gusty..  :(

Guess there is a problem with the light brightness in gusty.

---

### Post by horizontalung@eight on 2007-10-20
Hello,  I am also experiencing the same issues.  On my Gateway NX560X laptop, I upgraded from Fiesty to Gutsy - now I am experiencing issues with the screen brightness.  I have the Intel 945 graphics chipset and have been trying driver variations (I believe I was running on the i810 driver and am now using the Intel experimental driver).  I have noticed that if I adjust the screen brightness, at certain brightness percentages the backlight simply turns off (appearing to be a black screen).  There are about 4 points on the slider (including max brightness) where I can actually see the screen.  If anyone has any insight into this issue it would be greatly appreciated.

---

### Post by mabdelaziz on 2007-10-21
hey guys,
i have the same problem guys, gutsy on acer travelmate 6292...as soon as i unplug AC adapter, black screen.....it doesnt happen immediatly mind you, when i unplug the adapter, the screen starts dimming, and THEN turns off...i tried fighting it with H/W brightness keys...no go, i disabled "automatically dim screen"...still no go....

any help appreciated
thank you in advance =)

---

### Post by MRDutton on 2007-11-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/121833](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/121833) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The problem steams from the fact that your ACPI is reporting that your screen has brightness levels 0-100 but only levels 0, 12, 25, 37, 50, 62, ,75, 87 and 100 are valid. You can check this under /proc/acpi/video/XXX/brightness.

Because your ACPI told gnome-power-manager that it has 101 levels, G-P-M is trying to jump through them 5% at a time. Otherwise, you would presumably have to click the +brightness key up to 100 times.

At intervals of 5, the G-P-M brightness setting only lands on a valid setting 5 times (0, 25, 50, 75 and 100). When its on a invalid setting, its setting the brightness to zero because the sysfs interface used can't tell that it's invalid.

See [Bug #121833]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/121833") over at launchpad. There is some discussion about the problem and I posted a really ugly hack for the brave.

---

### Post by ruggersway on 2007-11-26
Thanks for the link to the bugtraq.  Good info.  It seems that there was an update that partially resolved this since the initial release.  I can switch to battery now without losing my display.  I can now move through my brightness levels and get 4 settings that work, it takes 5 times up or down to move to the next valid brightness.

It looks like this has been looked into pretty extensively via bugtraq, anyone know of a patch in the works to fix this?  I saw some hack fixes but I'm not bothered enough to put some hacks in place that could likely be broken or break future updates.

Thanks again

-rugger

---

### Post by madamore on 2007-12-01
I have a "compaq F506LA" notebook with kubuntu 7.10 gusty, and when I unplug the power cable had a black screen as result of using of "kde-guidance-powermanager" package.
Since I had not the same problem using vista in the same notebook, I installed "KPowersave" package and uninstalled "kde-guidance-powermanager", and problem solved.

I think you can do the same uninstalling "gnome-power-manager" and using an alternative one.

Thanks folks.

---

### Post by chrism66 on 2007-12-01
I messed with setting now I have the black screen, cant fix it have tried fail safe gome. Is there a way to to get my screen back?

---

### Post by madamore on 2007-12-02
what a I did to get back my screen was, move with de keyboard up and down since you start up your computer until you know that shout be in grub menu with out the timer working to start by default, then I unplugged and plugged the power cable a had my screen again.

Evidently this worked for me because I have a notebook.

---


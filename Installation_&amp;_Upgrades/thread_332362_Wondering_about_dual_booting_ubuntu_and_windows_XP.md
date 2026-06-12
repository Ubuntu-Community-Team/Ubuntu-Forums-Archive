---
title: "Wondering about dual booting ubuntu and windows XP"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by SlickTheNick on 2007-01-05
I downloaded a copy of ubuntu a while back to try it out via live CD, and thought it was great. The computer im on (only one in the house) is my mine and my familys computer, it has tons of games, several GBs of personal files, family photos, budgets etc. (all on windows XP). So clearly I cant simply just uninstall windows XP and go to ubuntu. But I really want to install it. So if I want to install it I have to dual boot XP and ubuntu.

Anyways im a little afraid of dual booting. I dont want my harddrive to get wiped somehow or anything like that, or become unbootable. I dont know if hes right, but my friend said that sometimes a computer/harddrive might not be able to dual boot, and I have no idea if my computer is compatible. I have a HP pavilion a810n computer which has a AMD athlon 64 3300+ processor in case anyone needs to know.

So ya, will I be able to dual boot ubuntu on this computer, and if so how can I do it safely so that there is practicly no chance that my harddrive will screw over on me? Im not exactly a idiot with computers (Im a web developer), im just very inexperienced with this sort of thing.

---

### Post by meng on 2007-01-05
Most likely you wouldn't have a problem dual-booting. However, you are advised to back up all valuable data before trying this, just to be on the safe side.

---

### Post by bukwirm on 2007-01-05
I've never had any problems with gparted (the partition editor included on the liveCD), however, if you're really concerned about your data, you could get a second hard drive and install Ubuntu on it - that would leave the first hard drive untouched.

---

### Post by SlickTheNick on 2007-01-06
Ya I think il save up and get a external harddrive, thanks guys :)

---

### Post by louieb on 2007-01-06
> **SlickTheNick said:**
> Ya I think il save up and get a external harddrive, thanks guys :)
Good idea. From one who has trashed an XP install with GParted.

---

### Post by Capt.Marion on 2007-01-06
I'm a geniune 110% Grade-A nub here. Is there some sort of switch to tell which hardrive to boot up to? I'd like to be able to boot to both my XP and my Kubuntu (if I do do this...). Also, can you have both booted at the same time and switch back and forth, or what?

---

### Post by MasterPatricko on 2007-01-06
The way it works is when the computer is booting up, after the POST etc. (where it shows the vendor logo and beeps and stuff), instead of going straight into loading windows as you are probably used to, a small text boot menu (either GRUB or LILO - by default grub) will come up. If you have ever had XP crash and the "do you want to boot into safe mode" menu came up, its a bit like that. The menu will say "Ubuntu-<kernel>" and "Microsoft Windows XP". The way this is all configured is from inside Ubuntu - the install auto-detects where XP is so it should be ready to go, and there is a graphical tool for further changes (something like Administration -> Boot Loader i think) or if you want to do it by hand the config file is /boot/grub/menu.lst - read the grub manual pages and it's self-explanatory.

Unfortunately the only way to switch between Ubuntu and Windows is by restarting the computer and choosing the other one from the boot menu. You can't have them both on at the same time. You could put one into hibernation I guess ... 
You can, of course, run Windows *inside* Ubuntu using emulation software, but that's completely different.

---

### Post by damispyderbyte on 2008-06-25
Hi this thread looks pretty old, but if you still read this here is my imput.

I have a HPa810n and ubuntu does not work correctly on it. For some reason the graphics driver does not work. Rhis issue is documented many times on the forums. Do not unstall unless you want no 3D.

Sorry this is so late :( 

Tyler

---


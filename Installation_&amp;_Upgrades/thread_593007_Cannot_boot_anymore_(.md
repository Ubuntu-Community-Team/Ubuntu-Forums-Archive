---
title: "Cannot boot anymore :("
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by andydrizen on 2007-10-26
Hi all, 

I installed Feisty last week on my Sony Vaio FE21B.. All was good until Gutsy came out.. After updating and restarting, my laptop wouldnt boot..

I had a dual boot set up, so I tried my windows partition.. that wouldnt boot either.

So I formated the HDD and put my Vista CD in - however, that get's to the same point every tiem I try, very early on in the install, and hangs.

I tried running the Ubuntu LiveCD, but that gets to the same point, then hangs.

I can use a Win98 Bootdisk and get in to command prompt and stay in DOS for as long as I like.. but I can't install any O/S's..

I took it to a repair shop who said the chipset may have been altered by Ubuntu - if this is true, does anyone know how i can change it back?

Thanks,

Andy

---

### Post by Pumalite on 2007-10-26
All you have to do is start afresh. DBan that hard drive:[http://dban.sourceforge.net/](http://dban.sourceforge.net/)
Then use Gparted Live CD and format the drive ntfs. Install the Windows of your choice. Then make space for Ubuntu (with Vista partitioner if using Vista)
Then install Ubuntu.
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by andydrizen on 2007-10-30
Thanks for the reply, although that didn't fix it.

I ran DBAN and Gparted, but when I put in the Vista CD it says "Loading Files" and a grey progress bar sits at the bottom of the screen ticking away.. When It completes, the Vista bootloader screen trys to appear, but only fades in about half way before the computer hangs.

With Ubuntu LiveCD, it loads a lot of files,then the screen goes blank with a blinking cursor in the corner, and then it hangs.

Gparted worked, and that is the closest thing I've seen to an operating system in ages.. 

Any thoughts? Andy

---

### Post by Pumalite on 2007-10-30
Did you format the drive ntfs with gparted after dban it? You can't install a Windows system without a drive already formatted ntfs.

---

### Post by andydrizen on 2007-10-30
yes i did

---


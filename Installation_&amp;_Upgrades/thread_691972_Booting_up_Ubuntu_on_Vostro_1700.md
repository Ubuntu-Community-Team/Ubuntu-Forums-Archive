---
title: "Booting up Ubuntu on Vostro 1700"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by LindaWu on 2008-02-09
Hi,

Before I start, I just wanted to say I'm really frustrated right now and I haven't even begin the installation process yet.

I recently purchased a Dell Vostro 1700 with the included Intel graphics card. I downloaded .iso files from the MIT Lab link from ubuntu.com's download list. I downloaded Nero 8 to burn my image files.

I used DVD+R to create my ubuntu live cd. I chose to burn once without the multisession option. 

After I burned the image file, I changed the bootup sequence on the Vostro and it won't boot. Windows Vista just keep loading over and over. I went as far as disabling all the boot options and only enabled CD/DVD drive boot. Still didn't work. Then I read somewhere in the forum that maybe Vista is being dumb and I need the alternate-text installer. I did that and burn it in Nero using the DVD-ROM [iso] option. Vostro still won't boot from the CD.

Ughhhhhhhhhhh. Ok, I apologize for the lack of professionalism in my tone but I'm just really mad right now.

Can anyone show me the light?

By the way, my CD/DVD drive works because I opened the CD/DVD drive in Windows Vista and it showed the ubuntu .iso file in there.

Thanks.

---

### Post by forceofnature on 2008-02-09
Did the ISO burn correctly?  I understand you can see the files but I would think there might be an issue with the ISO burn.  I loaded the Live CD on an HP laptop lastnight with no issues.  I also ran a verify on the CD in imgburn.

---

### Post by Pumalite on 2008-02-09
If you set CD as first in boot in your BIOS, you don't have a bootable CD. Follow this:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by zekica on 2008-02-09
> **LindaWu said:**
> By the way, my CD/DVD drive works because I opened the CD/DVD drive in Windows Vista and it showed the ubuntu .iso file in there.

You have to burn .iso image to CD, it means that you shouldn't create an empty data CD/DVD project and insert .iso in it, so that there is an .iso file on CD. You have to use **Burn image...** option in **Recorder** menu on Nero Burning ROM.

After you have done it, You should see more files on the burned CD, not just one .iso file.

---

### Post by twiddler on 2008-02-09
Press F-12 after powering your laptop, you should get an option to choose boot device. Select you DVD drive. If it doesn't boot, then something is wrong with your disk. download the alternate iso image.

---


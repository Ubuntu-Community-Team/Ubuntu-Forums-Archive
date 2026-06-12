---
title: "install on new asus g50v...HELP!!!"
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by zshift on 2008-08-09
Hi, I have the Asus G50V with the following specs:
intel core 2 duo t5750
pm45 chipset (centrino 2)
nvidia 9700m gt w/ 512mb gddr3
4 gb ddr2 800 (2x2gb)
seagate 200gb 7200rpm (2.5")
azalia audio, and atheros wireless n adaptor

when I try to install ubuntu, it goes all the way to partitioning the drives and transfering some data, but then itll crash with messages saying it can't read from certain location in page file. i have a 4gb swap partition i created during install, vista has ~150gb space, ubuntu would have ~26gb, also included is the asus expressgate software (linux os that takes less than 5 secs to boot) as first partition. 

after crashing it lands me in a root prompt, and anything i do causes the page file error to pop up. attempting to shutdown via `sudo shutdown -r now` causes an infinite number of these errors to occur. so far the only command that works is `help`.

please help me. im slightly familiar with linux terminal, but im more of a hardware guy so please be gentle...

also, i was trying to install the x86 version, regular desktop download. im downloading x64 as i write this and will try that later. :KS

---

### Post by Pumalite on 2008-08-09
You'll do better with 64 bit.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by WhiteFofito on 2008-08-10
I have the same laptop but i install ubuntu using the windows installing wizard becouse its the only way i found that works...

and about the drivers i didnt found nothing :( no graphic, no wireless no nothing just simple vga :(.

---

### Post by zshift on 2008-08-10
ive been searching the forums and so far of 3 people that have same laptop, all same issues...:(
only wubi installer seems to work with barely any driver support... :(
guess ill have to wait for better drivers or the next version of ubuntu/linux kernel that supports this...[-o<

---

### Post by eric3_14159 on 2008-08-20
Try changing the hard drive to compatability mode in the BIOS. I couldn't install from the liveCD without doing it, but after the change it worked just fine.

The graphics card works fine with nvidia-glx-new. The wired ethernet card needs the driver from Realtek ([http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=4&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#5,7,8,10,982](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=4&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#5,7,8,10,982)), and I haven't got the wireless ethernet card to work yet but the compat-wireless project ([http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)) looks promising.

---

### Post by Keymaster on 2008-09-02
If we can't get access to the internet how are we going to download the necessary files to compile the network driver?  Also can ndiswrapper help?  And how can I get my sound working?  Thanks

---


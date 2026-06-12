---
title: "can't install ubuntu 11.04"
date: 2011-09-30
forum: Installation &amp; Upgrades
---

### Post by anneblecforez on 2011-09-30
hi, im quite new to ubuntu...i want to install natty in my new notebook HP Pavillion G4 with 3bg RAM and 500gb hardisk. just bought it last month with windows7 in it. so i want to dual boot with natty. then i create a bootable usb with natty x86 and it succesfully installed but when i tried to boot it once again, i got blinking '_' on the top left of the screen. so i format it with active@killdisk. then i tried to install again but it freeze on ubuntu purple loading screen. i recreate the usb with x64 natty and install again. it still freeze on the purple screen. ive tried this about 10 times already. still freeze and sometimes i get this

> ~ unexpected exit with status 0x0009

then i run memory test (using the usb) and i have this :

> Memtest 86+ V4.10
Intel SNB 2095 MHz
L1 Cache  : 32 K        69845 MB/S
L2 Cache  : 256 K      31747 MB/S
L3 Cache  : 3072 K    23810 MB/S
Memory   : 3020 M    14652 MB/S
IMC   :  Intel(R) Core(TM)  i3 - 2310M  CPU @ 2.10GHz/BCLK : 8 MHz
Settings   : RAM  : 0 MHz  (DDR3-  0)

                                  1024K    e820        off

i have installed natty in my previous notebook ACER Aspire 4530 and it turns out ok. 
please help me.. i really need to use it..

---

### Post by Quackers on 2011-09-30
Welcome to UF :-)

Which graphics card is it using? You may need to use a boot option such as nomodeset until the correct graphics driver is loaded.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

How many PRIMARY partitions are being used in your system?
In Win 7 go to Disk Management screen for details.

---

### Post by vinterkind on 2011-09-30
Hi,

 > but it freeze on ubuntu purple loading screen

does it really freeze on the purple screen ?
Or could you press** [<CTRL>]<ALT><F3>** to get to another terminal ?

---

### Post by clausrei on 2011-09-30
Hi, 

I tried to install Ubuntu on a Toshiba notebook last year. Never ever I try this again. You did get a step further at least and could boot and install from USB. Get a proper Laptop ! Notebooks are a fiddle in any respect.

---

### Post by foresthill on 2011-09-30
Which specific HP Pavillion G4 do you have? There appear to be quite a few different models in this series.

---

### Post by pkg9991 on 2011-09-30
don't boot the Ubuntu in GUI but boot it in Recovery console and update the OS from there
then there will be 2-3 boot options for ubuntu with different shell versions try one of those, one will be working, rest all will be returning black screen or will be stuck at purple

---

### Post by anneblecforez on 2011-09-30
> Which graphics card is it using? You may need to use a boot option such as nomodeset until the correct graphics driver is loaded.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

How many PRIMARY partitions are being used in your system?
In Win 7 go to Disk Management screen for details.


i use ATI Radeon graphic and since i have format it there is no partition at all, no other OS at all.

> does it really freeze on the purple screen ?
Or could you press [<CTRL>]<ALT><F3> to get to another terminal ?

it really is freeze and ive never tried press that. where does it get me to?

> Which specific HP Pavillion G4 do you have? There appear to be quite a few different models in this series.

its HP Pavillion G4-1007TX.

---

### Post by Quackers on 2011-09-30
I'm a bit unclear now :-(
What have you formatted? You said earlier that you want to dual-boot Win 7 with Ubuntu but in your last post you say there is no other OS or partitions at all.

---

### Post by anneblecforez on 2011-10-02
> **Quackers said:**
> I'm a bit unclear now :-(
What have you formatted? You said earlier that you want to dual-boot Win 7 with Ubuntu but in your last post you say there is no other OS or partitions at all.

i format the whole thing, the laptop. it means that i deleted every single thing that has ever been in the laptop, win7, natty, files in it...everything...i did want to dual-boot it but like i said, after i tried to boot it once again, i got blinking '_' at the top left and that's why i formatted it. in short, there is no other OS or partitions at all (like a new bought notebook without any OS pre-installed in it).

---

### Post by anneblecforez on 2011-10-02
> **pkg9991 said:**
> don't boot the Ubuntu in GUI but boot it in Recovery console and update the OS from there
then there will be 2-3 boot options for ubuntu with different shell versions try one of those, one will be working, rest all will be returning black screen or will be stuck at purple

what does Ubuntu in GUI or Recovery console or shell version mean? can i do that because i can't even install natty. lets say it can, so does it mean i boot the installer (usb) then........ i don't know what to do.

---

### Post by Quackers on 2011-10-02
Ok, can you boot from the Natty live cd/usb and select "try Ubuntu"?

---

### Post by logiblocs on 2011-10-02
When you boot do you get a menu screen? If you do select recovery mode.

---

### Post by anneblecforez on 2011-10-02
> **Quackers said:**
> Ok, can you boot from the Natty live cd/usb and select "try Ubuntu"?

no. it gave me this

> 
~~unexpected exit with status 0x0009 			 		

---

### Post by anneblecforez on 2011-10-02
> **logiblocs said:**
> When you boot do you get a menu screen? If you do select recovery mode.

i think the recovery mode is when i have installed which i can't. the only menu i have is when i boot the natty live usb which is, - try ubuntu 
                                                        - install
                                                        - boot from hard disk
                                                        - advanced option
                                                        - test memory

---

### Post by anneblecforez on 2011-10-03
can't anyone help me? or do i have to send my laptop for repair? i really don't like the latter because it costs...

---

### Post by BillGod on 2011-10-03
I think what people are trying to get at is this.  If you boot from the usb drive and choose try ubuntu does it work?  If so then the problem should not be a hardware issue.  let everyone know if that works for you.  Then we can move on to other things to try.

---

### Post by anneblecforez on 2011-10-03
> **BillGod said:**
> I think what people are trying to get at is this.  If you boot from the usb drive and choose try ubuntu does it work?  If so then the problem should not be a hardware issue.  let everyone know if that works for you.  Then we can move on to other things to try.

no it doesn't work. i can choose the 'try ubuntu' then it will load with all the commands then it stop before it even get to the ubuntu purple loading screen. but if i choose install', then it will loads all the commands and then it freeze in the middle of the ubuntu purple loading screen. i don't think it a hardware issue because i just bought this and all i did was delete win 7.

---

### Post by Quackers on 2011-10-04
Have you checked the md5sum of the downloaded iso file?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by anneblecforez on 2011-10-05
> **Quackers said:**
> Have you checked the md5sum of the downloaded iso file?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

ive checked for both x86 and x64 iso. both said sums are the same..

---

### Post by anneblecforez on 2011-10-05
or do you guys think the issue here is the hardware?

---

### Post by goldshirt9 on 2011-10-05
> **Quackers said:**
> Welcome to UF :-)

Which graphics card is it using? You may need to use a boot option such as nomodeset until the correct graphics driver is loaded.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)


i'd try this , i have a similar problem .

---

### Post by anneblecforez on 2011-10-05
> **goldshirt9 said:**
> i'd try this , i have a similar problem .

i don't quite get what that forum said...the only part i get is choose 'try ubuntu' instead of 'install'. or is there anything else? you said you have similar problem, which means you can install and your laptop don't have any os?

---

### Post by anneblecforez on 2011-10-25
for about, what, a month?...i have installed an OS inside but its not natty, its lucid...i send it to someone and he installed it for me...the installation part is done...but now i have many other problems...cant two-fingers scroll, no sound at all, cant wake up after sleep...and Ive made a thread for the sound problem....hope you can see and help me...[http://ubuntuforums.org/showthread.php?p=11391529#post11391529](http://ubuntuforums.org/showthread.php?p=11391529#post11391529)

---


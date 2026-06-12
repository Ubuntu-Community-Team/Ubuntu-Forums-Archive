---
title: "Dual Booting Problem with Windows 8 and Ubutnu 12.10"
date: 2013-08-24
forum: Installation &amp; Upgrades
---

### Post by Cyb0rgz on 2013-08-24
Hi All,

Am beignner to Linux world. Tried to dual boot ubuntu along side preinstalled windows 8 in my samsung series 5 np550pc s03in Laptop.

I have followed this guide - [http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported) and based on the [video]("http://www.youtube.com/watch?v=wNCSbTyUzoM"), i have created a swap space and Ubuntu OS Space.

I have disabled Secure Bootloader and Booted in CSM. Everything went fine, ubuntu 12.10 installed fine and after restart, it doesnt booted up the ubuntu as well as Windows. Just a blank screen displays.

After restarting Ubuntu via LiveCD, I selected Try Ubuntu and installed Boot-repair. But still have booting problem.

Here is the pastebin link from boot loader -

[http://paste.ubuntu.com/6022524](http://paste.ubuntu.com/6022524)

Also, Please advice how much space should i allocate for Swap? I am going to allocate 200GB for Ubuntu and Hence advice the corresponding SWAP Size.

Please help me out. This booting problems cause me sick!

Thanks,
Cyborgz

---

### Post by Tobey666 on 2013-08-24
To your first question, did boot-repair give you any information about what was wrong/what it fixed when you ran it?
To your second question, according to the site: [https://help.ubuntu.com/community/SwapFaq#How_much_swap_do_I_need.3F](https://help.ubuntu.com/community/SwapFaq#How_much_swap_do_I_need.3F) the amount of swap needed is dependent on your computer. It gives the following example scenarios:

[COLOR=#333333][FONT=Ubuntu][FONT=inherit]_Low RAM and low disk space_[/FONT] With 512 MiB RAM and 30 GB hard disk, use 512 MiB for swap since RAM is very low.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit]_Low RAM and high disk space_[/FONT] With 512 MiB RAM and 100 GB hard disk, use 1 GiB for swap since RAM is very low and hard disk space is plentiful.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit]_High RAM and low disk space_[/FONT] With 2 GiB RAM and 30 GB hard disk, use 1 GiB for swap since hard disk space is very low.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit]_High RAM and high disk space_[/FONT] With 2 GiB RAM and 100 GB hard disk, use 2 GiB for swap since hard disk space is plentiful.

Given what you've told me about your laptop, the last example is probably the most relevant. [/FONT][/COLOR]

---

### Post by Cyb0rgz on 2013-08-24
Thanks for your quick response. 

I have run the boot-repair and it asks me to run some commands in the terminal. I just followed everything and finally it say boot repair is completed. It also displays the paste bin url and asked to verify after rebooting.
just a blank black screen got displayed and my Ubuntu CD got ejected.

After few mins, i have restarted it and says "Reboot and Select Proper Boot Device. or Insert boot media and Click Enter".

I have 8GB memory with 1 TH HDD - how can i update the swap space? i have already selected 1500 mb for swap space.

If the information provided in the pastebin is not sufficient, can you please let me know how i get more info (By running some cmd etc)? I Dont know what i have to do further? Thinking of installing it again. But not sure, whether the old files created by previous installation will cause problems.

Any idea mate? Please help me in dual boot windows 8 and ubuntu 12.10 (64 bit version)

---

### Post by Tobey666 on 2013-08-24
Honestly, I don't know how to solve this problem. It's way above my expertise level. The pastebin you posted suggests that the problem has to do with the way that your hard drive is partitioned. Re-installation is definitely an option--however it could be risky at this stage. Another possibility is to boot into a live version again and try running boot-repair again; it might detect some other problem that was created by the last repair.

---

### Post by oldfred on 2013-08-24
It looks like you originally turned on CSM/BIOS/Legacy boot in UEFI menu and booted Ubuntu installer in BIOS mode. Then it installs in BIOS mode, but you cannot easily dual boot with Windows as each time you have to go into UEFI, turn on UEFI to boot Windows and turn off UEFI and turn on CSM to boot Ubuntu.

Boot-Repair converted your install to UEFI and added grub into efi partition. Now with UEFI on and CSM off, you should have an ubuntu entry in UEFI to boot from. You have not installed secure boot version, but most systems will boot both Windows & Ubuntu with secure boot off. 

If you have one of the few that only boots Windows with secure boot on, then you have to boot Boot-Repair in secure boot mode and install the signed version of grub & the kernels.

If you reinstall boot in UEFI mode which will give grub menu not the accessibility icons.

If you have black screen issues that is video and not directly booting. You may then need nomodeset.

---

### Post by Cyb0rgz on 2013-08-25
> **oldfred said:**
> It looks like you originally turned on CSM/BIOS/Legacy boot in UEFI menu and booted Ubuntu installer in BIOS mode. Then it installs in BIOS mode, but you cannot easily dual boot with Windows as each time you have to go into UEFI, turn on UEFI to boot Windows and turn off UEFI and turn on CSM to boot Ubuntu.

Boot-Repair converted your install to UEFI and added grub into efi partition. Now with UEFI on and CSM off, you should have an ubuntu entry in UEFI to boot from. You have not installed secure boot version, but most systems will boot both Windows & Ubuntu with secure boot off. 

If you have one of the few that only boots Windows with secure boot on, then you have to boot Boot-Repair in secure boot mode and install the signed version of grub & the kernels.

If you reinstall boot in UEFI mode which will give grub menu not the accessibility icons.



Thank you so much for your explanation,i got a clear picture!!

I have UEFI enabled and Secure Boot Disabled and By Setting Ubuntu as High Priority for Boot. I got Booted Up With GRUB2 Menu showing Both Ubuntu and Windows!

Now I can Choose Windows/Ubuntu from GRUB Menu. But, I have few more Questions,

1.  During the Boot Order, i could notice Duplicate list of Ubuntu as shown in below snapshot. Can you please let me know how to remove the duplicate one?

  [ATTACH=CONFIG]245691[/ATTACH]

2.  In Grub2 Menu, I could Notice 4 Options. The Below Options 2.3 and 2.4 is odd for me. I choose 2.3 to boot into windows. But, is there any way i can have Ubuntu/ubuntu Advanced/Windows?

      2.1.Ubuntu
      2.2. Ubuntu With Advanced Menu
      2.3. Windows.XXX.Uefi.
      2.4. Windows uef config

3.  After Booting up, Ubuntu 12.10 file systems shows Windows Drive (C:/D:/ etc) and Also windows recovery Partition also. I would like to view only the Ubuntu File System Where i have installed Ubuntu os. Is that Possible?

4.  I have Allocated 200gb to ubuntu OS installation. Can i increase this more using some GUI tools? If changing those would have impact on boot loader? i mean some bootproblem?

5. Most Importantly, the Audio Volume is very low compared to same volume level which i have in Windows? I dont know whats the Actual Issue is.

6. How Can i update my Graphic Drivers GeForce GT 650M?

---

### Post by Andrew_Lucas on 2013-08-25
> **Cyb0rgz said:**
> Hi All,

Am beignner to Linux world. Tried to dual boot ubuntu along side preinstalled windows 8 in my samsung series 5 np550pc s03in Laptop.

I have followed this guide - [http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported) and based on the [video]("http://www.youtube.com/watch?v=wNCSbTyUzoM"), i have created a swap space and Ubuntu OS Space.

I have disabled Secure Bootloader and Booted in CSM. Everything went fine, ubuntu 12.10 installed fine and after restart, it doesnt booted up the ubuntu as well as Windows. Just a blank screen displays.

After restarting Ubuntu via LiveCD, I selected Try Ubuntu and installed Boot-repair. But still have booting problem.

Here is the pastebin link from boot loader -

[http://paste.ubuntu.com/6022524](http://paste.ubuntu.com/6022524)

Also, Please advice how much space should i allocate for Swap? I am going to allocate 200GB for Ubuntu and Hence advice the corresponding SWAP Size.

Please help me out. This booting problems cause me sick!

Thanks,
Cyborgz

Why are you using an out of date version of Ubuntu? 13.04 (which will be out of date in October, when 13.10 is released) is the latest version, 12.04 is the latest LTS release...I'd suggest getting rid of 12.10 and replacing it with an more up to date and/or stable release, and see if that fixes your problem. Out of date software is prone to bugs, especially on newer hardware.

---

### Post by Bucky Ball on 2013-08-25
@Andrew_Lucas: Wrong. Not sure where you got this info. 12.10 has an 18 month support cycle, until April 2014. Read this and keep as reference:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Please check accuracy of info before posting. Thanks. Carry on ... ;)

---


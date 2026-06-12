---
title: "Dual boot between vista and ubuntu? each located on a different hd?"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by fr0sty on 2007-12-01
Hi. I currently have Windows Vista: Home Premium (64 bit) installed on my Westren Digital 320GB HD. I unplugged it and then put Ubuntu on a Westren Digital 40GB HD and put that as my Master drive and the windows one as the slave. But wheneever i connect the windows hd as the slave, ubuntu won't load and i do not know how to fix this. I am a noob to ubuntu and would like to dual boot between vista and ubuntu using grub. The HD's work fine when separate, but when they are both hooked up at the same time, neither will load its os. In fact, the BIOS only picks up the master 40GB Hd with ubuntu on it, but it doesn't recognize the windows 320GB HD. This switches when I switch the physical position of the HDs. i don't want to edit the Windows drive in anyway in that I have lost my vista DVD and I am pretty sure it is gona be hard to find a 64 bit edition of home premium for free. If someone could tell me how I could maybe edit grub to have vista as a choice or how to just get my system to recognize both hds. I built this computer in May of 2007 and am pretty sure everything is up to date except for the second hd with ubuntu on it. That might be older. Thanks.

---

### Post by mouseboyx on 2007-12-01
You can probably press esc during the startup proccess and you can get to a boot menu for all the devices connected and choose the drive you want.

---

### Post by fr0sty on 2007-12-01
that didn't work and when i start up my computer with the windows hd attached only the ubuntu drvie shows up when i hit Esc. and after that ubuntu wont load if the windows drive is attached. what settings should i have on the hdds?

---

### Post by meierfra on 2007-12-01
Just to make sure that  I understand the situation:

However you plug in the drives, the bios only detect one drive?

If that is the case, I doubt that you will able to solve your problem.

But we can try:

Boot into ubuntut from ubuntu and post the output of

```
cat /boot/grub/menu.lst
```
and 

```
 sudo fdisk -l
```

(both "l" are lowercase L)

---

### Post by forestpixie on 2007-12-01
If vista boots when set as master I would do that and have ubuntu as the slave - then work from there if you're worried about losing your vista.

have a look [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

you can get easybcd from [here]("http://neosmart.net/dl.php?id=1")

further down on the ubuntu page there's this 

[Using the Desktop/LiveCD while preserving Windows Bootloader]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-09167948173503db5923da717a106f0c3aac1cd2") which might help you more.

Hope that helps some

---

### Post by adamite on 2007-12-01
Check your jumpers on both drives. Make sure your Ubuntu drive is the master and the Vista drive is the slave. The diagram for the setting the jumpers should be on the labels of both drives. After setting the jumpers on both drives, go into the BIOS when you power on the PC and check to see if both drives are correct. If they are, save the configuration. The PC will reboot and GRUB should come up with both your Ubuntu and your Vista setup.

Vista will appear on other Operating Systems. Try Vista bootup first, then Ubuntu. I did the same way for mine with Ubuntu and Win98.  Hopefully, that should do it. If no luck, there are other threads how to change GRUB to bootup both Ubuntu and Vista.

---

### Post by fr0sty on 2007-12-01
Hey thank you guys so much. I finally found out was that I put both drive settings as "Cable Select" and put the Vista one on the Master and the Ubuntu one on Slave. When I booted up the BIOS found both drives and I am happy that I can just press F8 to choose which drive to boot from, I may be a Windows fan because of all of my friends and school uses it, but Ubuntu really kicks but in that it boots way faster than Vista and I know that I would have never had such great help if I had looked to Microsoft for support. i am now a dedicated user to both vista and Ubuntu. Thanks for all of the help.

---

### Post by ginormusus on 2007-12-01
on my other pc there is the main drive slot and the slave drive spot, so make sure the slave drives connected in the secondary slot

---

### Post by KMW on 2007-12-02
frOsty,
I am having the same problem and have tried your solution w/o any luck.
I'm using 7.10 and XP. Jumpered as 7.1 master and XP slave. Checked Bios and reset boot order to CD First, hd0 second and hd1 third. ESC key only shows Ubuntu and F8 does nothing.

Anyone with any other advice?

---

### Post by fr0sty on 2007-12-02
Well I originally heard that the Ubuntu drive had to be the master and when I did that, only that one would show up, and if the vista one was attached as the slave, the ubuntu one wouldnt start up. I recoment making sure that both of your HDDs on the back are set to CS (cable select). Then make the microssoft one the master on the cable connection and the ubuntu one on the slave. When you boot up, it will automatically go into xp, but you can get to a HDD selection menu if you just push F8 until a window pops up allowing you to choose a hdd to boot from and they wont interfere with each other. this also prevents your windows from being affected. Also, unhook your xp drive from the computer when installing ubuntu on the second HD cause it wiped out my friend's xp. If I can post a pic i will do so and show how my physical setup is since its kinda hard to picture without seeing it in action.

Good Luck

---

### Post by fr0sty on 2007-12-02
I havent tried the ESC key but I bet it works. i have a picture that I would like to submit but don't know how to upload it to the net minus getting a bunch of junk programs on my vista comp. KMW if you could post a program that you use to upload/ share pictures then I could get that and just send this too you. If you have a facebook page I already have it uploaded, but I am not so sure you could have one and i am not so willing to put my name out.

---

### Post by baxterdog on 2007-12-02
Just as an add-on to this thread I would like to add the idea of checking the hard drive dip switch (the .1 inch connections in the back af the drive) Some drives are auto master and some aren't. Look up your particular drive for the corrcect jumper setting.

---

### Post by lenswipe on 2007-12-10
hi all

im having booting issues with vista/ubuntu but not in the same way The issues i have is that i tried to follow [this]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")


however at the part where it says about vista/longhorn

> On the "Ready to install" screen, you'll see that Ubuntu now has enough information to commence the installation. In the summary under Migrate Assistant, it should say "Windows Vista/Longhorn (loader)". This means that regardless of whether Ubuntu found any user account to migrate, it certainly knows that Windows Vista is installed on the other partition and is aware of it. Click Install.

on my computer it just says Migrate Assistant:

it doesnt say vista/longhorn this presumably means that it hasnt detected windows vista and therefore may or may not delete it....

Horrible as windows vista is i need the data on that partition because thats where alot of my files are...

Please dont tell me to back up all my things because i really dont have time.


Please just telll me what i need to do and also if all my data is likeley to be wiped (i didnt choose the "use entire disk option" but the fact that it clearly couldnt detect vista makes me a little unsure.


Please help!!

---


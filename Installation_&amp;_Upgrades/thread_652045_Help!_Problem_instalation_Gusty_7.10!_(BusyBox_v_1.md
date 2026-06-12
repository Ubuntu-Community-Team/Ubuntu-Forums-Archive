---
title: "Help! Problem instalation Gusty 7.10! (BusyBox v 1.1.3)"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by Tecka on 2007-12-28
Hi! Im new in the forum... Im from argentina and i dont speak so well English, so yo have to help me... xD
Im new with Linux and im trying to install Ubuntu Gusty Gibbon 7.10 on my PC.
I have windows too in te same PC, so i made a partition In the Same Disk.. (One Disk of 80 GB) with 2 partitions (one of aprox 55 Gb(Format NTFS) with Windows XP and the other with 20Gb(Format EXT 2) for linux) and In the partition of 20 gb i made another partition of 1GB for the Swap.... I have the Live cd and i have Installed all.... In the end of the Instalation, when it want me to restart the pc, I restart But when y have to Choice (afther the boot) only apears me the Windows XP and Linux Ubuntu (A friend have Ubuntu and to him appears WinXp an a lot of Ubuntu configurations, etc....) OK. I put Linux and it start to charge.... after it appears me a black screan which have a text... (I dont remember so well, I only remember the title) BusyBox v 1.1.3. And there I can write a command: "Help" (it describe the Program) If I put Help It appears a long text.:confused:
I have been reading and Searching a lot and I think this is a common problem but I dont now how to fix.
Now Im Downloading the Alternate CD for try another thing but I dont know.....:-k
Please help!!! Im really lost Whith this... This problem will sick me if a dont fix. :mad:
                                            Sorry for my writing.... Thanks, and Bye from Agentina. ):P

---

### Post by LunatikOwl on 2007-12-28
Try to type:
```
sudo /etc/init.d/gdm restart
```
or:
```
 sudo startx 
```
and post us the output. If you want some command to output to a file(so you could copy/paste the file contents to here) you can type:
```
 <command> > filename
```
e.g ```
 sudo startx > output
```
Also, could you post your hardware information like CPU type, Motherboard, graphics card etc.?

---

### Post by Tecka on 2007-12-28
OK... But where do you want me to type the commands?? Im now in Wndows. Linux  only i can install the live(?) (I Install Linux On windows with the live cd, I restart and Enter to Ubuntu with the CD....) Yo want me to type the commands on the console?? I Undestand right¿?

PC:
Processor: AMD Semprom 2800 + 1.6 GHz
Mother Board: Biostar K8M800 Micro AM2 / K8VGA-M
256Mb Ram x 2 
Hard Disk 80 Gb Sata x 2
Video Card: Nvidia Geforce FX 5200

If you need somthing more said.....

---

### Post by xeth_delta on 2007-12-28
Hola y bienvenido/a al forum!

Can you please tell us the name of the CD you installed from? Are you sure it was a desktop CD?

---

### Post by Tecka on 2007-12-28
(BienvenidO)  Gracias.....
 
The Cd Name is: Ubuntu 7.10
I think he didnt put i386 because it was too long for the label of the CD 

But if you`re saying that the cd is wrong... No is the Answer. A friend who give me the cd install from there.... So... I dont know what to do. If you anybody can help me I will grateful him/her.

---

### Post by xeth_delta on 2007-12-28
You have to try what LunatikOwl suggested in the command line you are presented after booting Ubuntu. Give it a try and let us know what happens.

---

### Post by Tecka on 2007-12-28
MMMM.... I will try in 1 hour aprox... Im downloading the alternate cd....
But The commands which LunatikOwl give me... Where does he want me to type?? In the "BusyBox"
(that black screan that I described????)

---

### Post by xeth_delta on 2007-12-28
> **Tecka said:**
> MMMM.... I will try in 1 hour aprox... Im downloading the alternate cd....
But The commands which LunatikOwl give me... Where does he want me to type?? In the "BusyBox"
(that black screan that I described????)

That is right, in the busybox screen.

---

### Post by Tecka on 2007-12-28
OK. thanks... When a download finish I will try...
    I will post the results.

---

### Post by Tecka on 2007-12-28
Well.... I Try with the commands But Nothing....

Now I take a foto of the error, so, you can see and say what is happening.....

[IMG]http://img144.imageshack.us/my.php?image=p1010554yk7.jpg[/IMG]

If you dont see the image, this is the link: [http://img144.imageshack.us/my.php?image=p1010554yk7.jpg](http://img144.imageshack.us/my.php?image=p1010554yk7.jpg)

---

### Post by xeth_delta on 2007-12-28
> **Tecka said:**
> Well.... I Try with the commands But Nothing....

Now I take a foto of the error, so, you can see and say what is happening.....

[IMG]http://img144.imageshack.us/my.php?image=p1010554yk7.jpg[/IMG]

If you dont see the image, this is the link: [http://img144.imageshack.us/my.php?image=p1010554yk7.jpg](http://img144.imageshack.us/my.php?image=p1010554yk7.jpg)

Ok, I got the image. It seems to be stopping when loading the initramfs image.

Try the following when you are prompted with the grub image:
-place the selection to linux and press the "e" key.
-append to the end of the line the text: init 1
-press the ENTER key to save.
-press b to boot.

Let us know what happens.

Xeth

---

### Post by Tecka on 2007-12-28
Please I need to fix this, so if yo see, and you know anything that can work, Post here.
     Thanks xeth_delta for your helping and continue searching....

---

### Post by Tecka on 2007-12-28
Well xeth_delta I send a PM to you whith a Question about the Console or Menu of Grub.... And with my personal mail to make it works better.

---

### Post by Pumalite on 2007-12-28
With 256 MB of RAM, I'd give this a try:
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
Or this:
[http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)

---

### Post by Tecka on 2007-12-28
Nonono.. Pumalite I dont have 256 of ram... I have 2 Cards of 256.. so I have 512 MB...
Of the hadware, I think, is not the problem... My friend, who give me the cd, installed Whith exactly the same Hadware.... All is the same.

---

### Post by Pumalite on 2007-12-28
Sorry, I thought one of the first posts mentioned 256 of RAM. Forget it then.

---

### Post by Tecka on 2007-12-28
Its OK... And you have somthing else to aport??
                 Tecka

---

### Post by Pumalite on 2007-12-28
Let me review the thread...

---

### Post by Pumalite on 2007-12-28
I think the problem is your graphics card. If you do a search in the forum, you'll get a lot of hits.

---

### Post by xeth_delta on 2007-12-28
> **Tecka said:**
> Well xeth_delta I send a PM to you whith a Question about the Console or Menu of Grub.... And with my personal mail to make it works better.

Got it. I sent you back a PM.

---

### Post by Tecka on 2007-12-29
Well... I want to try with the alternate CD but I dont know how to prepare the cd.... I downloaded the CD.. If you Know, please tell me how to do it. 
                                                Tecka

---

### Post by Pumalite on 2007-12-29
It's an iso like the others. Burn it as an image, at 4x, in good quality CD-R media.
It's very easy to install.

---

### Post by Tecka on 2007-12-29
well... I have burn ... but I didn know that I have to do as an image.... I emule the image whith Daemon tools and Copy the disk.
I will try the other posibility. Thanks

---

### Post by Tecka on 2007-12-29
Yeah!!!!!!! I burned the cd!!! It works!
 But when I put the option for see the integrity of the cd it said this:

> The 
-pool/restricted/n/nvidia-kernel-common/nvidia-kernel-common_20051028+1ubuntu7_all.deb  file failed the MD5 Cheksum verification.
The CD or the file may have been corrupted 

So, I have problem whith the Video Card (like Pumalite Said yesterday)....

How can I fixed???
Why this file is corrupted??

Thanks, and all the information than can help me is welcome.
                       Tecka

---

### Post by Pumalite on 2007-12-29
Did you do an md5sum on the iso before burning?
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by Tecka on 2007-12-30
Well..... I burned the cd whit all the programs that you give me Pumalite Now the CD is ok And I did all the instalation success, But after the boot of the machine, the black Screen, were I should select one of the sistems(Windows XP or Linux), Dont appears.  It starts directly WinXP, with no time or question to me to select One of them.

 Pumalite or anybody have an answer to this problem???
 
                                                     Thanks, Tecka.

---

### Post by xeth_delta on 2007-12-30
This is strange. Was perhaps grub not installed? Where did you chose to install grub when asked?

---

### Post by Tecka on 2007-12-30
In the principal disk or something like that...

---

### Post by Pumalite on 2007-12-30
When you get to the blank screen, try this:
Ctrl+Alt+F1 to get a command line. If you get one:
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose 'vesa' as the driver, then: startx

---

### Post by Pumalite on 2007-12-30
If it doesn't work, reinstall, making sure you do md5sum first and later check CD for integrity before you install. Burn at 4x.

---

### Post by Tecka on 2007-12-30
MMM... The black screen doesnt appears.. so, I cant select one of the sistems, it start Windows.

I did all the steps for burn the cd. The Cd is not the problem I think.

---

### Post by xeth_delta on 2007-12-30
Does the alternate cd allow for just starting to a command line without installing?

---

### Post by Tecka on 2007-12-31
Mmmm.... I dont remember, But I dont think so....

---

### Post by xeth_delta on 2007-12-31
If that is not the case, download a live CD, verify the image integrity, and burn it. Let us know if there's any problem.

Happy new year to all!
Xeth

---

### Post by ienthach on 2008-01-03
i have same problem as Tecka. Please help me.

---


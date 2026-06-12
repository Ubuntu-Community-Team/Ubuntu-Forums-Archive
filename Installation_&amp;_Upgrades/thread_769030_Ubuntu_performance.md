---
title: "Ubuntu performance"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Roman10 on 2008-04-26
Hi people, 

after many years who I take [COLOR="Red"]only[/COLOR] Microsoft's software (from dos to Vista) I decide to try the alternatives to this OS. 

I have downloaded Ubuntu and I see that is very nice OS and I began to see all the functions with curiosity and a with a certain kind of enthusiasm. But when I start some functions all together like Mozilla, Messanger and Audio player (how I do before in the Microsoft OS) the system go too slowly and sometimes itself close mozzilla and play very badly the songs.

I think too that I don't have a bad hardware system... I have do a report with a benchmarking software and I do see to you

[See Here]("http://gr.rossoalice.alice.it/fmc/antefrm.php?filename=/PUBLIC/hardinfo_report.html.")

I have a bad hware system? Or I have do something wrong to configure my Ubuntu? (indeed I don't have touch nothing about configuration)

thanks to whoever would answer and excuse me for my English

---

### Post by Pumalite on 2008-04-26
Non poso vedere. Excuse my Italian.

---

### Post by kellemes on 2008-04-26
The link isn't working..
Your hardware-specs indeed may shine some light on things..

---

### Post by Roman10 on 2008-04-26
> **Pumalite said:**
> Non poso vedere. Excuse my Italian.

> **kellemes said:**
> The link isn't working..
Your hardware-specs indeed may shine some light on things..

Thank you for your answer.

[See Here]("http://www.gigasize.com/get.php?d=t0ovkv8lv7b")

---

### Post by Pumalite on 2008-04-26
Same thing. Just post your specs.

---

### Post by Roman10 on 2008-04-26
> **Pumalite said:**
> Same thing. Just post your specs.

Ok. (is the best thing)

Intel Pentium 4 - 2,8 Ghz
Ram - 1 Gb (I think ddr 300, but I don't remember in a sure way)
2 Hard disk
- Maxtor Sata 250 Gb (where is ubundu)
- Maxtor Ide 120 Gb
Graphic card nVidia 256 Mb (but like the ram, I'm not sure)

Thank for your patience

---

### Post by Roman10 on 2008-04-26
> **Pumalite said:**
> Same thing. Just post your specs.

Ok. (is the best thing)

Intel Pentium 4 - 2,8 Ghz
Ram - 1 Gb (I think ddr 300, but I don't remember in a sure way)
2 Hard disk
- Maxtor Sata 250 Gb (where is ubundu)
- Maxtor Ide 120 Gb
Graphic card nVidia 256 Mb (but like the ram, I'm not sure)

Thank for your patience

---

### Post by Pumalite on 2008-04-26
Have you installed an Nvidia driver?

---

### Post by Roman10 on 2008-04-26
> **Pumalite said:**
> Have you installed an Nvidia driver?

Yes. Is the only thing who I have touched because I have read that Ubundu can't modify this driver and I must install the nVidia drivers.

---

### Post by Pumalite on 2008-04-26
The only other thing that occurs to me is your mix of SATA and IDE. Where do you have your OS's?. Post:
sudo fdisk -l

---

### Post by Roman10 on 2008-04-26
> **Pumalite said:**
> The only other thing that occurs to me is your mix of SATA and IDE. Where do you have your OS's?

On Sata. If I put Vista on this hd, it works very well (but I can't activate it for a lot of reason)


> . Post:
sudo fdisk -l

:shock:

What?

Thank you again for your patience

---

### Post by Pumalite on 2008-04-26
Copy and paste the command in your Terminal and copy and paste the output in here.

---

### Post by Roman10 on 2008-04-26
> **Pumalite said:**
> Copy and paste the command in your Terminal and copy and paste the output in here.

[CENTER][IMG]http://img170.imageshack.us/img170/4407/screenshotiz0.png[/IMG][/CENTER]

---

### Post by Pumalite on 2008-04-26
Mount the partrition:
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
Post:
cat /media/sdb1/boot/grub/menu.lst

---

### Post by Roman10 on 2008-04-26
> **Pumalite said:**
> Mount the partrition:
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
Post:
cat /media/sdb1/boot/grub/menu.lst

I gotta write all this things on terminal? (excuse me, but remember that I have used only Microsoft systems until now ).

Thanks

---

### Post by H4rm0ny on 2008-04-26
Yes.

Enter:
```
sudo mkdir /media/sdb1
```

as the first line (it will probably ask you for your password). Then
```
sudo mount -t ext3 /dev/sdb1 /media/sdb1
```

And then post for us the output of the following command:
```
sudo mkdir /media/sdb1
```

Actually, if it looks like the second line threw an error, you could post the output of that one as well.

---

### Post by Pumalite on 2008-04-26
The Terminal is the most powerful instrument in your Linux OS. Learn to use it. Tutorials:
[http://www.ubuntugeek.com/tag/ubuntu-hacks/](http://www.ubuntugeek.com/tag/ubuntu-hacks/)
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)
[http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)
[http://howtoforge.com/taxonomy_menu/1/1/50](http://howtoforge.com/taxonomy_menu/1/1/50)
[http://www.littleigloo.org/tutorial.php3](http://www.littleigloo.org/tutorial.php3)
[http://www.geekgirls.com/](http://www.geekgirls.com/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)

---

### Post by Roman10 on 2008-04-26
> **H4rm0ny said:**
> Yes.

Enter:
```
sudo mkdir /media/sdb1
```

as the first line (it will probably ask you for your password). Then
```
sudo mount -t ext3 /dev/sdb1 /media/sdb1
```

And then post for us the output of the following command:
```
sudo mkdir /media/sdb1
```

Actually, if it looks like the second line threw an error, you could post the output of that one as well.

Thank you Harmony for being involved in this discussion! I have do this steps. And now?

> **Pumalite said:**
> The Terminal is the most powerful instrument in your Linux OS. Learn to use it. Tutorials:
[http://www.ubuntugeek.com/tag/ubuntu-hacks/](http://www.ubuntugeek.com/tag/ubuntu-hacks/)
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)
[http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)
[http://howtoforge.com/taxonomy_menu/1/1/50](http://howtoforge.com/taxonomy_menu/1/1/50)
[http://www.littleigloo.org/tutorial.php3](http://www.littleigloo.org/tutorial.php3)
[http://www.geekgirls.com/](http://www.geekgirls.com/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)

Really thanks guys. In italian forum I cannot find all this kindness.

---

### Post by H4rm0ny on 2008-04-26
> **Roman10 said:**
> Thank you Harmony for being involved in this discussion! I have do this steps. And now?

Oh crap! I'm really sorry - I posted the wrong line. After doing those first two commands, the last line should be:
```
cat /media/sdb1/boot/grub/menu.lst
```

This should display some information which we'd like you to copy and paste for us to see. It will tell us information about how your computer is booting.

Don't worry - you don't have to redo the first commands again. Just do the line above and give us the output. Sorry!

-Harmony.

**EDIT:** It will probably be quite a lot of information. Make sure you get it all. ;)

---

### Post by Roman10 on 2008-04-26
[CENTER][IMG]http://img293.imageshack.us/img293/8296/96137297wc0.png[/IMG]
[IMG]http://img177.imageshack.us/img177/1049/37274365jz5.png[/IMG]
[IMG]http://img177.imageshack.us/img177/2531/85293139qe3.png[/IMG]
[IMG]http://img405.imageshack.us/img405/1162/34075807gl2.png[/IMG][/CENTER]

I think is all!

---

### Post by Pumalite on 2008-04-26
Change this:
title Vista
rootnoverify (hd0,3)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by Roman10 on 2008-04-26
> **Pumalite said:**
> Change this:
title Vista
rootnoverify (hd0,3)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
savedefault
makeactive
chainloader +1

I must apply this change ever in the terminal?

---

### Post by GTengineer on 2008-04-26
Roman u can select, copy and paste text from the terminal without having to take and post screenshots. It will probably make your life easier in the future.

---

### Post by Pumalite on 2008-04-26
Are you runing the installed Ubuntu or the Live CD now?

---

### Post by Roman10 on 2008-04-26
> **GTengineer said:**
> Roman u can select, copy and paste text from the terminal without having to take and post screenshots. It will probably make your life easier in the future.

It's true. It's a my custom with Windows because I had a very simply software..

> **Pumalite said:**
> Are you runing the installed Ubuntu or the Live CD now?

Excuse me... but I did not understand perfectly. Now is running Ubuntu. What is the Live CD?

---

### Post by H4rm0ny on 2008-04-26
> **Roman10 said:**
> I must apply this change ever in the terminal?

The command "cat" that you just ran on the file "/media/sdb1/boot/grub/menu.lst" showed us the contents of that file. Pumalite wants you to change the file to contain what he posted. There are lots of ways to do this, but the easiest way for you is as follows:

Open the file "/media/sdb1/boot/grub/menu.lst" by typing the following in the terminal:

```

sudo ls
sudo gedit /media/sdb1/boot/grub/menu.lst &
```

*(The sudo ls isn't needed for itself, but it ensures you have entered the password if it is needed, before you launch the next command - don't worry about this now).*

A window should open displaying the file you just posted for us by using the cat command. You can edit this very easily. But be careful - this is an important file. It might be best to save a copy of it somewhere as well. Pumalite wants you to change the section near the end where it has a block starting "title Vista" so that it looks like what he has posted. But let us know if you're not sure what to change.

By the way, you don't have to post screenshots. You can actually copy the text from the terminal by highlighting the lines you want with the mouse and then selecting "Copy" from the Edit menu. Much neater. ;)

Hope this helps.

---

### Post by Roman10 on 2008-04-26
Really, really, really **_[COLOR="Red"]thanks[/COLOR]_** guys.

Now I need to reboot system?

---

### Post by Roman10 on 2008-04-27
> **Roman10 said:**
> Really, really, really **_[COLOR="Red"]thanks[/COLOR]_** guys.

Now I need to reboot system?

hello forum.

I have rebooted the system and nothing is change.

](*,)

---

### Post by ssam on 2008-04-27
install the package
```
preload
```
with synaptic [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

this speeds up program loading by preloading your most used programs into ram

---

### Post by diebels on 2008-04-27
Hi Roman.
I think you where led a bit on the wrong track here.

I saw your hardware report, and part of it says:
```
OpenGL
Vendor	Mesa project
Renderer	Mesa GLX Indirect
Version	1.4 (2.1 Mesa 7.0.3-rc2)
Direct Rendering	No

```
I think that is the cause of your performance problems.

Somehow the high performance drivers for the nvidia graphics card did not get installed correctly.

How did you install these drivers. Was it from the System -> Administration -> Hardware drivers menu?

---

### Post by Roman10 on 2008-04-27
> **ssam said:**
> install the package
```
preload
```
with synaptic [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

this speeds up program loading by preloading your most used programs into ram

Excuse me. But I dont understand. Why I need to load applications on ram when my hware theoretically should go in a good way with Ubuntu? 

> **diebels said:**
> Hi Roman.
I think you where led a bit on the wrong track here.

I saw your hardware report, and part of it says:
```
OpenGL
Vendor	Mesa project
Renderer	Mesa GLX Indirect
Version	1.4 (2.1 Mesa 7.0.3-rc2)
Direct Rendering	No

```
I think that is the cause of your performance problems.

Somehow the high performance drivers for the nvidia graphics card did not get installed correctly.

How did you install these drivers. Was it from the System -> Administration -> Hardware drivers menu?

I think that I have updated drivers.

[CENTER][IMG]http://img373.imageshack.us/img373/8774/screenshotxz6.png[/IMG][/CENTER]

---

### Post by diebels on 2008-04-27
> **Roman10 said:**
> 
I think that I have updated drivers.

[CENTER][IMG]http://img373.imageshack.us/img373/8774/screenshotxz6.png[/IMG][/CENTER]

Yes, looks like they are installed correctly. There could be a bug stopping them from getting loaded up on startup though.

There is a simple benchmarking program called glxgears. Just type glxgears into a terminal. If get a couple of thousand fps everything is working right.

Also "glxinfo | grep direct", should give a yes result. And "grep -i nvidia /var/log/Xorg.0.log" should give you a lot of info and no errors.

---

### Post by Roman10 on 2008-04-27
glxgears give me between 900/1100 Fps ever 5 second... is good?

---

### Post by Roman10 on 2008-04-29
Hi guys, I have formatted my hd and re-installed Ubuntu.

I have noticed one thing: my pc works in a good way with offline applications (Gimp, OpenOffice, Amarok,etc) because I tried to open a lot of applications to do this test (and the sys is fast), but I have problems when I start a web application (Mozilla, aMule, etc). 

It may be the problem of the system performance? 

I use an Usb wireless support and maybe the system need the original drivers.

Somebody can help me to search (and install especially) this kind of drivers?

(The support is a d'link G122 usb)

Thanks to all

---


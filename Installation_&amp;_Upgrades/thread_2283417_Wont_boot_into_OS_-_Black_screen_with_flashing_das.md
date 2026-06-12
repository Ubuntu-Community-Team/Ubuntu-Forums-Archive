---
title: "Wont boot into OS - Black screen with flashing dash"
date: 2015-06-21
forum: Installation &amp; Upgrades
---

### Post by joey_tbf on 2015-06-21
After upgrading to the newest ubuntu. I am unable to boot into the OS

All i see is a black screen with a flashing dash

I am able to go into the boot grub

What can i do?  I am new to ubuntu

---

### Post by joey_tbf on 2015-06-21
I forgot the photos
[Img]http://i61.tinypic.com/1589zrp.jpg[/img]

[IMG]http://i62.tinypic.com/2jca9ua.jpg[/IMG]

---

### Post by Bashing-om on 2015-06-21
joey_tbf; Hello;

Did you install a proprietary graphics driver ? Then we can suspect highly that the driver became broke in the update process.

What results when you boot the "recovery" console ?
From the functional recovery console we can look at the state of the system;

Then decide on what action to take.

[INDENT][INDENT]fault isolation
[/INDENT][/INDENT]

---

### Post by joey_tbf on 2015-06-21
I'm not sure if it installed a graphic driver. It was working before.

I went into:  3.16.0-38-generic recovery mode

And this is what i see. 

[Img]http://i57.tinypic.com/s49a9u.jpg[/img]

I am on my mobile and i dont have another computer.

---

### Post by Bashing-om on 2015-06-21
joey_tbf; Hey;

Let's try an easier means maybe to "see" :
in this recovery console choose "networking" .This will also enable write mode to the file system and then choose"root" so we have access to a terminal.
In this terminal what returns:
```

ubuntu-drivers devices
ubuntu-drivers list

```
As I consider this a graphics driver issue.

[INDENT][INDENT]else. will do something else
[/INDENT][/INDENT]

---

### Post by joey_tbf on 2015-06-21
I pressed yes. But then It seems i got an error

[IMG]http://i61.tinypic.com/30tibt2.jpg[/IMG]

[IMG]http://i57.tinypic.com/2efklft.jpg[/IMG]

---

### Post by Bashing-om on 2015-06-22
joey_tbf; Well;

Surprised that you were unable to reach the GUI - even if it would have been in a degraded state. 
Be aware, looks as if you have encryption in effect for the file system, I have no experience with this level of complexity. But, we can try a more direct approach to boot the system.

Try:
At the grub boot menu with the normal ubuntu kernel selected, press the 'e' key for edit mode -> boot options screen. Arrow down to the line starting with 'linux' and arrow across to the terms "quiet splash" and also add the term nomodeset . Press key combo ctl+x to continue the boot process using the fall back graphics driver. Can you now boot to the GUI . Again a degraded state is OK at this point .

IF you can login and gain the desktop, what results :
Software Center -> Software Sources in the top panel menu -> Additional Drivers in the last tab. Install the recommended driver for the graphics set.
Reboot to see the effect .

[INDENT][INDENT]maybe now ?
[/INDENT][/INDENT]

---

### Post by joey_tbf on 2015-06-22
Can you tell me what this part means:

arrow across to the terms "quiet splash" and also add the term nomodeset .

I found the words quiet splash. 

But im not sure what arrow accross means and im not sure how to add it and where to add it.

---

### Post by joey_tbf on 2015-06-22
Do you mean add nomodeset after quiet splash?


So it should look like this:


...... -vg-root ro quiet splash nomodeset $vt_handoff........

---

### Post by joey_tbf on 2015-06-22
If so....

I just tried that and after pressing ctrl+x it went to a black screen. 

The lcd is on but just a black screen with nothing on it. :(

---

### Post by Bashing-om on 2015-06-22
joey_tbf; Hummm ..

Not at all the expected result ! ..

OK, let's see if we can boot to terminal. Instead of the boot parameter "nomodset" replace "quiet splash' with the term text.
key combo ctl+x to continue to TTY1.
login here with username and password.
AND I have to wonder what part encryption plays in this ??

Can do ?

[INDENT][INDENT][INDENT]sometimes I wonder
[/INDENT][/INDENT][/INDENT]

---

### Post by joey_tbf on 2015-06-22
After following those instructions. I dont get any login page. 
All i see is this:
[IMG]http://i58.tinypic.com/28rh3ip.jpg[/IMG]

Sorry about the picture upside down. But im doing this from my cellphone as i dont have another computer.
and i dont know why my cellphone did that.

---

### Post by Bashing-om on 2015-06-22
joey_tbf; Yuk;

Regrets but I am out of ideas. I do not know now how to get the system booted.

[INDENT][INDENT]sad state of affairs
[/INDENT][/INDENT]

---

### Post by joey_tbf on 2015-06-22
After several tries i got into the boot screen

[IMG]http://i58.tinypic.com/2unydrs.jpg[/IMG]

---

### Post by Bashing-om on 2015-06-22
joey_tbf; Great !


As we now have a terminal. we can proceed and find out what is not taking place .

The graphics situation:
what returns from terminal commands:
```

ubuntu-drivers devices
ubuntu-drivers list

```

and also let's verify that "you" are authorized to access your /home directory:
```

ls -al .Xauthority
la -al .ICEauthority
l -al /home

```
It should be something similar to mine - where I am "sysop" :
```

sysop@1404mini:~$ ls -al .Xauthority
-rw------- 1 sysop sysop 209 Feb  4 15:15 .Xauthority
sysop@1404mini:~$

sysop@1404mini:~$ la -al .ICEauthority
-rw------- 1 sysop sysop 326 Jun 22 12:51 .ICEauthority
sysop@1404mini:~$

sysop@1404mini:~$ l -al /home
total 28
drwxr-xr-x  4 root  root   4096 May 19  2013 ./
drwxr-xr-x 25 root  root   4096 Jun 16 17:30 ../
drwx------  2 root  root  16384 May 19  2013 lost+found/
drwxr-xr-x 29 sysop sysop  4096 Jun 22 12:51 sysop/
sysop@1404mini:~$ 

```

[INDENT][INDENT]on the road to recovery
[/INDENT][/INDENT]

---

### Post by joey_tbf on 2015-06-22
Here is the result


[IMG]http://i61.tinypic.com/sngkky.jpg[/IMG]

---

### Post by Bashing-om on 2015-06-23
joey_tbfl ; HoKay ;

Authorization is proper, so we are looking at the graphics driver as the issue here.

As ubuntu-drivers commands are not supported, we look from another set of commands:
```

lspci -vnn | grep VGA -A 12
sudo lshw -C display

```

See then what we are working with, and what we work toward.


[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by joey_tbf on 2015-06-23
Here is the outcome

[IMG]http://i60.tinypic.com/3ro80.jpg[/IMG]

[IMG]http://i58.tinypic.com/289lafb.jpg[/IMG]

---

### Post by Bashing-om on 2015-06-23
joey_tbf; Well well .........

Intel graphics, very well supported in ubuntu; and they "just work" and the driver is installed and inuse .
So, let's see what hints we can get to direct our attention when we start the desk top from this terminal.
```

sudo service lightdm start

```

See what the logs also have to relate:
1st Install our pastebin tool:
```

sudo apt-get install pastebinit

```
```

cat /var/log/Xorg.0.log | pastebinit
cat ~/.xsession-errors | pastebinit

```
the results of "pastebin" is a URL back to terminal. Pass the URL back here to the thread and I will access it to read those logs.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by joey_tbf on 2015-06-23
I did not work. It says 

Job not started

Pastebinit has no installtion candidate

 [IMG]http://i58.tinypic.com/nwakg1.jpg[/IMG]

---

### Post by joey_tbf on 2015-06-23
Wahhhhhh.  Im so sad:sad:

---

### Post by Bashing-om on 2015-06-23
joey_tbf; Huh ???


What release are you running and what desktop ????

pastebinit is available in 14.04's main software repository :
```

sysop@1404mini:~$ apt-cache show pastebinit
Package: pastebinit
Priority: optional
Section: misc
Installed-Size: 164
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Rolf Leggewie <foss@rolf.leggewie.biz>
Architecture: all
Version: 1.4-3
Replaces: bikeshed (<< 1.21)
Depends: python3
Recommends: lsb-release
Breaks: bikeshed (<< 1.21)
Filename: pool/main/p/pastebinit/pastebinit_1.4-3_all.deb
<snip>

```

Now I got to scratch my head on this !

[INDENT][INDENT][INDENT]sometimes again I do wonder
[/INDENT][/INDENT][/INDENT]

---

### Post by MAFoElffen on 2015-06-23
Please slow down.

The commands he is giving you have a carraige return / enter key between them. <> You have had multiple post showing where you have entered multiple commands as if they were one command. That is why your output is getting errors of unrecognized arguments.
```

ubuntu-drivers devices
ubuntu-drivers list
lspci -vnn | grep VGA -A 12
sudo lshw -C display

```
The commands above are actually 4 separate commands. You mistakenly entered them on the commandline as:
```

ubuntu-drivers devices ubuntu-drivers list
lspci -vnn | grep VGA -A 12 sudo lshw -C display
```
So they should be either entered as 4 seperate commds (As first noted) --OR-- If you are going to string them together, put "&&" between them, which will say do the previosu to this first, then when it finshes, excute the following command, like this:
```

ubuntu-drivers devices && ubuntu-drivers list && lspci -vnn | grep VGA -A 12 && sudo lshw -C display

```



What i see is that you are running 14.10 and have an Intel graphics APU. Intel drivers are opensource, meaning that Intel provides the source code for their video drivers to their own graphics hardware to the Linux community. This has worked well in the past, but is not full-proof. Every once in a while, they do make mistakes with their own code.

As mention before, try to use nomodeset as a boot up option in the grub Linux boot line. You could also use either "modeset.i915=0" or "video=[port]:[Resolution],[OtherOptions]" kernel boot option as described in post #1 of my sticky (link in my sigline). Also ensure that you have not disabled Intel by using any modprobe blacklisting within /etc/modprobe.d/ or /usr/lib/modprobe.d/ for any i915 drivers.

EDIT-- If any of that resolves your issue, tell us and we will instruct you on how to make that work-around persistent. (If that is it, it is just a temporary fix until a fix can be applied to the opensource drivers. For that to happen, we will need you to make a bug report to Launchpad. That will trigger an upstream bug report to Intel, for them resolve the issue in their code.)

---

### Post by Bashing-om on 2015-06-23
@MAFoElffen :D

So pleased you dropped in !

How is your masters coming along ?

[INDENT][INDENT]a little help goes a long way 
[/INDENT][/INDENT]

---

### Post by MAFoElffen on 2015-06-23
So far, so good. Friday night was graduation commencement for this school: AAS in Programming, AAS in Database Management, AAS-T in Computer Science w/ Programming Emphasis, Certificate of Proficiency in Web Design. Continuing with BS in Programming and BS in Database Management. (Leaning towards Systems Programming.) Helping my son with a systems management system for a mixed server (MS & Linux) environment.

---

### Post by joey_tbf on 2015-06-23
You mean like this?



...... -vg-root ro quiet splash modeset.i915=0 $vt_handoff........

---

### Post by joey_tbf on 2015-06-23
ahhhh. I give up. This is too hard nothings works

---

### Post by MAFoElffen on 2015-06-23
Yes. Just a little patience please. Help us to help you. You are getting it. I see that just by what you have done so far.  

And if you remove the "quiet splash $vt_handoff=7"... then you could see the text messages that display during the boot. If you see some errors in those messages, they may hint to what may be going on.

---

### Post by Bashing-om on 2015-06-23
joey_tbf; Hey ;

+10 ^^; Patience . We do understand. Look, learning a new operating system is a lot like learning a new language when you get down, as we are, to the "nuts and bolts" . 
The great thing about ubuntu is that if/when the frustration/time element gets to great, one backs up their data and (RE-)installs the operating system. Done in just a matter of minutes. Back up and operational. HOWEVER, doing this one learns little or nothing.

If you are unwilling to make the effort then there is little we can do. Believe me, help is what we do. If at anytime you do not understand by all means ask the question(s). There is nothing more important that that of you understanding . And given the time and effort and a liveDVD there is nothing in this operating system that in not fixable. Though sometimes that path to a solution is unclear. It can be found . Time effort and frustration. The rewards are well worth it .

Our present conditional is to install 'pastebinit' and post those logs for our review to find that path to resolution.
As we have a operational terminal that does indicate the foundation of the operating system is stable. Now it is just a matter of layers, and what is taking place in the layer that is the GUI . 

We practice 
[INDENT][INDENT][INDENT]fault isolation to restoration.
[/INDENT][/INDENT][/INDENT]

---

### Post by joey_tbf on 2015-06-23
No matter how many times i try. I cant install pastebinit

[IMG]http://i62.tinypic.com/2mcipl2.jpg[/IMG]

Ive also tried

modeset.i915=0
modeset.i915=1
modeset.i915=2
modeset.i915=3

And removed the "quiet splash $vt_handoff"

---

### Post by MAFoElffen on 2015-06-24
I traced the error in your last post as from kernel source file ../drivers/thermal/intel_soc_dts_thermal.c. I think the exception was thrown by this code:
```

if (err) {
-        pr_err("request_threaded_irq ret %d\n", err);
-        goto err_free;

```
That source file had to do with adding Intel Braswell CPU support (Intel HD grasphics) and APIC IRQ. So it seems like the error is from a modifiable trip from the Intel device driver helper files internal to the kernel.

You said this worked previously right? With the error you are getting and what this source file is about... I have a couple ideas for you to try. 
1st-- Try adding "noapic" as a kernel boot option.
2d-- From the Grub Boot Menu, boot from a previous version kernel.

---

### Post by joey_tbf on 2015-06-24
Where exactly do i add "noapic"

vg-root ro quiet splash noapic $vt_handoff

Like that?

I booted from these 2 but the same problem occurs
[Img]http://i61.tinypic.com/1589zrp.jpg[/img]

---

### Post by Bashing-om on 2015-06-24
joey_tbf; Hey .

Thank goodness for Mike's coding skills !
Yes, you have the right of it to make the boot edit " vg-root ro quiet splash noapic $vt_handoff "
If that does not boot up then try to boot with the older kernel :
At the grub boot menu you arrow down to the entry of " with linux 3.16.0-38-generic" - an asterisk will be to the left of the enty -and press the enter key.


[INDENT][INDENT]try try again
[/INDENT][/INDENT]

---

### Post by joey_tbf on 2015-06-24
I tried noapic and different kernal's  but still get a black screen.

---

### Post by Bashing-om on 2015-06-24
joey_tbf; Well ..

2 steps forward and 3 back . We really need to see these logs. Presently I can not fathom why 'pastebinit' is not found to be able to install it.

Lets make sure the system is up to date and the package manager is in a happy state.
Boot back to terminal ( text in grub boot parameter) and run terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

```
If that completes with no errors we proceed on and try once more to install pastebinit:
```

sudo apt-get install pastebinit

```

[INDENT][INDENT][INDENT]gotta be a reason; gotta be a cause
[/INDENT][/INDENT][/INDENT]

---

### Post by joey_tbf on 2015-06-25
It worked!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

[http://paste.ubuntu.com/11771601](http://paste.ubuntu.com/11771601)
[http://paste.ubuntu.com/11771604](http://paste.ubuntu.com/11771604)

---

### Post by Bashing-om on 2015-06-25
joey_tbf; Hey, Hey !

Persistence do pay off !

OK, now we know the reason, but it is presently over my skill set to know the cause .
When it is all said and done by the operating system:
> 
125.691] (EE) Failed to load module "vesa" (module does not exist, 0)
[   125.691] (EE) No drivers available.

we wind up with an inability to load any graphics drivers . I have no experience with the Intel chip set so I have to do some home work to find out how to find out what is not taking place.

Maybe just as simple as (RE-)installing xserver-xorg (-core) components ??

I will be back.

[INDENT][INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-06-27
joey_tbf; Welp ....

In light of the fact no one else has a better idea, let's (RE-)install  some xorg components.
```

sudo apt-get install --reinstall xserver-xorg-core xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri 
sudo dpkg-reconfigure xserver-xorg 
sudo shutdown -r now

```

Do you now come back up with a functional GUI ?

[INDENT][INDENT][INDENT]It could happen
[/INDENT][/INDENT][/INDENT]

---

### Post by joey_tbf on 2015-06-27
It did not work. 

I got an error message with the first command

Something about unmet dependiences

[IMG]http://i60.tinypic.com/2h7mfqv.jpg[/IMG]

---

### Post by joey_tbf on 2015-06-27
What happens if i upgrade?  Maybe it will re-install the files

I will try this:
do-release-upgrade

---

### Post by Bashing-om on 2015-06-27
joey_tbf; Welp:

> 
What happens if i upgrade? Maybe it will re-install the files

I will try this:
do-release-upgrade


In my opinion, though it "might" install/upgrade what is broke, generally NOT a good thing to try and release upgrade a system that is not fully upgraded and fully functional ( and all PPAs reverted) . 

I am disappointed the effect was not as desired.
But, here we make progress, we have an error advisory we can work with:
Let's see what happens in addressing the error :
```

sudo apt-get install libglapi-mesa

```

If that goes well we try again to (RE-)install the xorg components .

[INDENT][INDENT]try try again
[/INDENT][/INDENT]

---

### Post by joey_tbf on 2015-06-27
Sir!!  I am so sorry. I broke it even more.  I did the sudo upgrade command before i seen your message that i shouldn't do it. 

Now it seems to be more broken.


When i start my computer i am seeing this screen

[IMG]http://i62.tinypic.com/aws23d.jpg[/IMG]

---

### Post by joey_tbf on 2015-06-28
Here is my new pastebin

paste.ubuntu.com/11786370
paste.ubuntu.com/11786373

---

### Post by Bashing-om on 2015-06-28
joey_tbf; Yukkie;

The screen shot is the boot messages. And no problem is indicated to the time the photo was taken.

Do you boot to the GUI ?
If not Can you boot to terminal ? - The method to boot to terminal in release 15.04 differs from prior releases.

Be aware that release 15.04 uses systemd now rather than upstart as the initiate system to boot up and control services.
I have very limited experience or knowledge of systemd.  Nor does my sphere of experience include (L)ogical (V)olume (M)anagement OR encryption.

Others now must pick up my slack. 


[INDENT][INDENT]all in all
[INDENT][INDENT][INDENT][INDENT]UNgood
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by joey_tbf on 2015-06-28
I can boot to the terminal. I cant go into the backup video driver

---

### Post by joey_tbf on 2015-06-28
[IMG]http://i62.tinypic.com/2mhu5pg.jpg[/IMG]

---

### Post by joey_tbf on 2015-06-28
[IMG]http://i62.tinypic.com/xd80lv.jpg[/IMG]

---

### Post by joey_tbf on 2015-06-28
It worked!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!


I was able to log in!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by joey_tbf on 2015-06-28
I used your code:



Code:
sudo apt-get install --reinstall xserver-xorg-core xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri 
This was successful


sudo dpkg-reconfigure xserver-xorg 
but this failed. So i used this code
sudo apt-get install xserver-xorg


sudo dpkg-reconfigure xserver-xorg
Then this finally worked

Then this
sudo shutdown -r now


When i logged in. It said ubuntu encontered a problem.

But now it works!!!!!!!!!!!!!!

---

### Post by Bashing-om on 2015-06-28
joey_tbf; WOW !

What a load off the mind !

Let's now make sure the package manager is in a happy state, and the file system - from the package manager's view point - is consistent .
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg -C

```

And what release are you up on ?
```

lsb_release -a
cat /etc/issue
unname -r

```
[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]when it hurts, it will tell you
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by joey_tbf on 2015-06-29
hello sir!!

At the moment i am unable to see what version i am on. I believe i was on 15.1

I am not using ubuntu anymore.  After you fixed my ubuntu, i deleted it an installed windows. 

I deleted ubuntu because i needed to use windows for other applications such as photoshop and qq and skype. 

I plan to install ubuntu again when i return home, but at the moment i am not home.  So i need my laptop for work

And i did learn alot.  Hopefully when i return home i will install ubuntu along side with windows. So i can keep learning more.  

My mission is to learn linux.   I feel i learned lots with that week you were helping me.  But i am not sure if i understood what i did. 

Thank you very much for helping me fix it.  Now i have a laptop again.

---

### Post by Bashing-om on 2015-06-29
joey_tbf; WHelll;

> **joey_tbf said:**
> hello sir!!

At the moment i am unable to see what version i am on. I believe i was on 15.1

I am not using ubuntu anymore.  After you fixed my ubuntu, i deleted it an installed windows. 

I deleted ubuntu because i needed to use windows for other applications such as photoshop and qq and skype. 

I plan to install ubuntu again when i return home, but at the moment i am not home.  So i need my laptop for work

And i did learn alot.  Hopefully when i return home i will install ubuntu along side with windows. So i can keep learning more.  

My mission is to learn linux.   I feel i learned lots with that week you were helping me.  But i am not sure if i understood what i did. 

Thank you very much for helping me fix it.  Now i have a laptop again.

I will not deny that is one solution.
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

When you are in the position to take up this linux learning curve, we are here to help.

[INDENT][INDENT]it is a thing
[/INDENT][/INDENT]

---


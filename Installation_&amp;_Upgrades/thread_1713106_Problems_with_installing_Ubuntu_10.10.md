---
title: "Problems with installing Ubuntu 10.10"
date: 2011-03-23
forum: Installation &amp; Upgrades
---

### Post by trendyabinash on 2011-03-23
Sir, i have downloaded the Ubuntu 10.10 Desktop edition. As my desktop's CD drive is not working, i decided to use a flash drive to install. Formatted the Flash drive (4gb) with HP formatting tool as FAT32 file format. Uploaded the image using the Universal USB installer from pendrivelunix's site. The flash drive working fine it can see the initial boot menu, but once i select run Ubuntu or install Ubuntu it is not working :(

Anyway i can provide the result ? or any help regarding this would be much appreciated.

---

### Post by trendyabinash on 2011-03-24
I tested the Flash drive (pen drive) on my laptop and it is perfectly fine, Ubuntu is starting on the laptop, byt not starting on my desktop :(
please help me

---

### Post by wilee-nilee on 2011-03-24
There are two initial choice screens the second of which is only try or install. The first to be seen needs the shift key held down immediately on booting the thumb. If you get to that one hit f6 and choose nomodeset and boot in. This is a low graphics login you may need graphics drivers once installed.

Once installed you would at the grub menu hit e and replace at the kernel the splash with nomodeset to get in again to find the drivers.

Just guessing here.

---

### Post by trendyabinash on 2011-03-24
ty i will try and let you know

---

### Post by trendyabinash on 2011-03-24
My system is hanging at 0.6 something. is there a way to get a log file of whats happening ?

EDIT :
I noted down the last line of the booting process

[0.718354] [<c010363e>] Kenrnel_thread_helper+0x6/0x10

after this the lights of CAPSLOCK and SCROLL LOCK of Keyboard starts blinking and nothing happens. Probably hanging i guess.

---

### Post by Hakunka-Matata on 2011-03-24
Welcome to the Forum trendyabinash/Sir:

I have a suggestion for you, I've used 10.10 32bit Desktop, and I like it.  7.04 was the  first steady version of GNU/Linux Ubuntu I used.  Now the suggestion:

[LIST]
[*]Download and install [http://cdimage.ubuntu.com/releases/natty/alpha-3/](http://cdimage.ubuntu.com/releases/natty/alpha-3/) and try it instead of, or in addition to 10.10 (maverick)
[*]For quickest relief, choose [http://cdimage.ubuntu.com/releases/natty/alpha-3/natty-desktop-amd64.iso.torrent](http://cdimage.ubuntu.com/releases/natty/alpha-3/natty-desktop-amd64.iso.torrent)
[*]to download .iso (above link)
[*]use unetbootin to write the .iso to USB.  Download it [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[/LIST]
Please Sir, if you do not mind, report on how you like 11.04 natty?  If you have a 64bit capable CPU, use the amd64 bit version.  

COMMENTS:  11.04 is the cleanest installing, best Release yet AFAIAC.

recommended programs to add first, to make the subsequent initial work more pleasant are:


[LIST=1]
[*]projectM (in synaptic)
[*]vlc (in synaptic)
[*]open vlc, select 'streaming' do next step, pasting the copied link into the streaming URL
[*]go to interweb URL [http://www.radioparadise.com/content.php?name=Listen](http://www.radioparadise.com/content.php?name=Listen) click on and copy the [COLOR=Blue]128 AAC [COLOR=Black]link, return to [/COLOR][/COLOR]vlc, paste link into streaming URL.  Start the MUSIC
[/LIST]
for listening SIR, cheers.

Ave a Gday

---

### Post by trendyabinash on 2011-03-24
> **Hakunka-Matata said:**
> Welcome to the Forum trendyabinash/Sir:

I have a suggestion for you, I've used 10.10 32bit Desktop, and I like it.  7.04 was the  first steady version of GNU/Linux Ubuntu I used.  Now the suggestion:

[LIST]
[*]Download and install [http://cdimage.ubuntu.com/releases/natty/alpha-3/](http://cdimage.ubuntu.com/releases/natty/alpha-3/) and try it instead of, or in addition to 10.10 (maverick)
[*]For quickest relief, choose [http://cdimage.ubuntu.com/releases/natty/alpha-3/natty-desktop-amd64.iso.torrent](http://cdimage.ubuntu.com/releases/natty/alpha-3/natty-desktop-amd64.iso.torrent)
[*]to download .iso (above link)
[*]use unetbootin to write the .iso to USB.  Download it [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[/LIST]
Please Sir, if you do not mind, report on how you like 11.04 natty?  If you have a 64bit capable CPU, use the amd64 bit version.  

COMMENTS:  11.04 is the cleanest installing, best Release yet AFAIAC.

recommended programs to add first, to make the subsequent initial work more pleasant are:


[LIST=1]
[*]projectM (in synaptic)
[*]vlc (in synaptic)
[*]open vlc, select 'streaming' do next step, pasting the copied link into the streaming URL
[*]go to interweb URL [http://www.radioparadise.com/content.php?name=Listen](http://www.radioparadise.com/content.php?name=Listen) click on and copy the [COLOR=Blue]128 AAC [COLOR=Black]link, return to [/COLOR][/COLOR]vlc, paste link into streaming URL.  Start the MUSIC
[/LIST]
for listening SIR, cheers.

Ave a Gday

Thank you for your tips Sir. But i wanted to use a stable version and not one in alpha stage, reason is simple i am not that professional user of Ubuntu/Linux. I am very much interested in learning.

Now coming back to the problem, any ideas what i am facing here ?

---

### Post by symioun on 2011-03-24
hi ,
  i m trying to install aircrack-ng but it shows like this,
king@king-Virtual-Machine:~$ sudo apt-get install aircrack-ng
[sudo] password for king: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package aircrack-ng

---

### Post by Hakunka-Matata on 2011-03-24
Are you using the 'nomodeset' option?

Also, I suggested the 11.04 because it may well step right thru your install procedure, I say that from experience, they have Alpha3 to a state that is very good, already.  Might save you work.  It's **quite stable** already.

---

### Post by Hakunka-Matata on 2011-03-24
> **symioun said:**
> hi ,
  i m trying to install aircrack-ng but it shows like this,
king@king-Virtual-Machine:~$ sudo apt-get install aircrack-ng
[sudo] password for king: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package aircrack-ng

@symioun:

Welcome to the Forum:  Please start your own thread.

:D

---

### Post by trendyabinash on 2011-03-24
> **Hakunka-Matata said:**
> Are you using the 'nomodeset' option?

Also, I suggested the 11.04 because it may well step right thru your install procedure, I say that from experience, they have Alpha3 to a state that is very good, already.  Might save you work.  It's **quite stable** already.

i am not able to find that option sir, can u please tell me how i can see it ?

---

### Post by Hakunka-Matata on 2011-03-24
I'll tell you if you'll promise me to try what I suggested?

---

### Post by trendyabinash on 2011-03-24
hahaha ok deal. btw just to see whether other version or Ubuntu works or not i had the image of Ubuntu 9.04 which i tried to run on my desktop too. But same results. Is my desktop's hardware not supported ?

Earlier everything was working fine, recent changes i did to my desktop is New wireless card and graphic card, earlier i had Nvidia 7100GS Now ATI RADEON HD 5450

---

### Post by trendyabinash on 2011-03-24
/etc/init.d/rc 390 ----input output error... there is a list of these coming out :(

And the boot is terminated

---

### Post by Hakunka-Matata on 2011-03-24
OK, tell me where your installation stops?, freezes?

---

### Post by Hakunka-Matata on 2011-03-24
Your video vga card is not in the default drivers of that installation, probably

```

das@d-a-s-1104-64:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon 3100 Graphics
das@d-a-s-1104-64:~$ 

```

---

### Post by trendyabinash on 2011-03-24
I am not even able to reach to the part where i can start installation, i used the UNetBootin u said to make the USB installer/Live. Iget the Selection screen
1. Default
2. Help
3. Try Ubuntu without any change to your computer.

i select the 3rd option, i see Ubuntu and the dots below it, like loading then it takes me to console showing a lot of input/output errors :(

If i do it on my laptop there is nothing it works great

---

### Post by Hakunka-Matata on 2011-03-24
> **trendyabinash said:**
> I am not even able to reach to the part where i can start installation, i used the UNetBootin u said to make the USB installer/Live. Iget the Selection screen
1. Default
2. Help
3. Try Ubuntu without any change to your computer.

i select the 3rd option, [COLOR=Red]i see Ubuntu and the dots below it[/COLOR], like loading then it takes me to console showing a lot of input/output errors :(
If i do it on my laptop there is nothing it works great

When you see [COLOR=Red]that[/COLOR] screen, try Hitting the TAB key

And by the way, Your SYSTEM IS STARTING the installation, it just halts ....

---

### Post by sadiqdude on 2011-03-24
> **symioun said:**
> hi ,
  i m trying to install aircrack-ng but it shows like this,
king@king-Virtual-Machine:~$ sudo apt-get install aircrack-ng
[sudo] password for king: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package aircrack-ng

what network card u are using?????

---

### Post by trendyabinash on 2011-03-24
Ok i managed to install it. by pressing shift key after selecting an option.

But now i got another problem, i.e. when i am trying to connect to wireless network it is asking me for a "Unlock Keyring" and i don't know what to give. It says it is locked and i have to enter a password

---

### Post by Hakunka-Matata on 2011-03-24
it's the same password as your Ubuntu logon password

And we can edit some configuration to stop that from happening

---

### Post by trendyabinash on 2011-03-24
ty very much for your support sir.

I am having few troubles with setting up my wireless card. I guess I will start another thread for it ?

Also i had to re-format my PC again b'coz the Windows setup was corrupted after installing Ubuntu 10.10

---

### Post by Hakunka-Matata on 2011-03-24
What was wrong with the Windows Partition?

You must be getting quite comfortable with partitioning and installing by now!!!!  That's how I learn also, repetition is good.  Thank you Sir;

Cheers, 

I want to hear what was wrong with the Windows installation pls.

---

### Post by Hakunka-Matata on 2011-03-24
You would get help with your wireless here too, but of course if it's a real tricky problem you'd have more experienced people over in that section.  What is the wireless problem?

---

### Post by trendyabinash on 2011-03-24
After installing Ubuntu, it showed that it has installed my wireless card's drivers but was unable to connect to router.

About Windows i have no idea, on grub screen if i select to start windows then all i saw was blank screen

---

### Post by Louisraritan on 2011-03-24
Have you tried using the 10.04 lts image instead?

---

### Post by trendyabinash on 2011-04-08
Thank you very much for the help guys. pressing F6 while booting Ubuntu 10.10 solved my problem

I tried 11.04 as was advised to me and it is working now.

I am having problem with installing graphic card this time but on 11.04. Have made a post for it [http://ubuntuforums.org/showthread.php?p=10652009#post10652009](http://ubuntuforums.org/showthread.php?p=10652009#post10652009)

Marking this as solved.

---


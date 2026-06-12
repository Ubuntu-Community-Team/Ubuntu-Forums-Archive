---
title: "blank screen trouble"
date: 2004-12-19
forum: Installation &amp; Upgrades
---

### Post by abstractism on 2004-12-19
hello all, I just installed ubuntu linux on my PC. sick of the altogether lameness of windows etc etc...I finished with the installer and it restarted and there was no video output. normally I wouldn't come to you guys with my problem already but I can't get anything to work and I dunno how to change stuff when there's no video output. here's my specs:
athlonXP 2800+
msi KT4V-L motherboard
1gb kingston hyperx pc2700
256mb ATI radeon 9800 pro
original installation of ubuntu linux + security updates and such that the installer wanted to download.

anyway, can anyone help me out here?[-o<  I'm a linux n00b here. thanks.

---

### Post by Rancoras on 2004-12-19
At what point do you lose the video?  Can you see any error messages before you lose it?

---

### Post by abstractism on 2004-12-20
after it shows the startup routine, it changes resolutions as if to show the desktop background(like other OSes do) and my CRT stops recieving graphic output.

---

### Post by Rancoras on 2004-12-20
Sounds like it didn't detect your monitor correctly.  Try booting into recovery mode so you can check the monitor section of your X config file.  Make sure the settings match the specs for your monitor.  You can find them in your owners manual or the manufacturers web site.

---

### Post by abstractism on 2004-12-20
aheh...I don't have the manual. I bought my 21" CRT at a computer show.  8-[ 

can anyone tell me what I need for it to work right? I like it at 1280x1024 at 24-bit color(32?) with a refresh rate of 70(I think)

---

### Post by Rancoras on 2004-12-20
Did you look on the manufacturer's web site?

---

### Post by abstractism on 2004-12-20
nope. I'll check it out after werk today :)
its a dell CRT

---

### Post by next_gener on 2004-12-20
[QUOTE=Rancoras]Sounds like it didn't detect your monitor correctly.  Try booting into recovery mode so you can check the monitor section of your X config file.  Make sure the settings match the specs for your monitor.  You can find them in your owners manual or the manufacturers web site.[/QUOTE]
 im haveing the same probs here! im in recovery mode but i dont know any commands to get or change the info here, what do í type or what do i do?

Also got a 21" monitor and the info from the manufacturer!

Any help is greatly appreciated! Thanks!

---

### Post by Rancoras on 2004-12-20
[QUOTE=next_gener]im haveing the same probs here! im in recovery mode but i dont know any commands to get or change the info here, what do í type or what do i do?![/QUOTE]

Try this after you log in:

```
sudo nano /etc/X11/XF86Config-4
```

That should open your X config file in nano.  Nano is a pretty simple editor, the key commands are listed at the bottom.

Look for the section with the HorizSync and VertRefresh settings for your monitor.  Make sure they match the specs for your monitor.  Change them if needed, save the file and reboot.

---

### Post by next_gener on 2004-12-21
ok, what do i do now, im a newb too! LOL

I got a screen which i can navigate using L-Alt and letters but i dont know whats what! 
If i hit Get Help it asks for a line but when i enter it i get "Come on be reasonable", what am i doing wrong?

Thanks for helping!

EDIT:

When in recovery mode it says root@ubuntu:~ # and i presume i type "login" but when i do it says "ubuntu login:" and i enter my username, password, name, name of computer and it fails all of them! is there something i have to enter here to get further? i can type the sudo nano command above (not when it says ubuntu login though) but like i said, i dont know what to do here! 

Thanks for any help!

---

### Post by Rancoras on 2004-12-21
[QUOTE=next_gener]I got a screen which i can navigate using L-Alt and letters but i dont know whats what! 
If i hit Get Help it asks for a line but when i enter it i get "Come on be reasonable", what am i doing wrong?[/QUOTE]

Alt+G is a "go to" shortcut.  It's asking what line to go to.  You will notice that the letter shortcuts at the bottom of the window are all preceded by the ^ symbol.  That symbol means press the CTRL key.  If you want to read the help then you would press CTRL+G.

[QUOTE=next_gener]When in recovery mode it says root@ubuntu:~ # and i presume i type "login" but when i do it says "ubuntu login:" and i enter my username, password, name, name of computer and it fails all of them! is there something i have to enter here to get further? i can type the sudo nano command above (not when it says ubuntu login though) but like i said, i dont know what to do here! [/QUOTE]

Sorry, I was a little vague. When you use the recovery mode, you are already logged in.  So just issue the nano command in the earlier post at the prompt.

---

### Post by next_gener on 2004-12-21
OK, got it now but what do i do when i have run the command? I dont know what to edit or change or view! 

Sorry for the questions but im new to this!

What i need is a simple explanation so i can learn what im doing as im doing it! 

Thanks again for helping!

---

### Post by Rancoras on 2004-12-21
As I said:

[QUOTE=Rancoras]Look for the section with the HorizSync and VertRefresh settings for your monitor.  Make sure they match the specs for your monitor.  Change them if needed, save the file and reboot.[/QUOTE]

What these settings do is tell X the frequencies for your particular monitor.  If they are set out of your monitor's range, then your monitor displays nothing.  This is what I suspect at this point.  Change them to match what your manufacturer says they should be.  Then you save the file and reboot, hopefully you see the GDM login screen after that.

---

### Post by next_gener on 2004-12-21
[QUOTE=Rancoras]As I said:



What these settings do is tell X the frequencies for your particular monitor.  If they are set out of your monitor's range, then your monitor displays nothing.  This is what I suspect at this point.  Change them to match what your manufacturer says they should be.  Then you save the file and reboot, hopefully you see the GDM login screen after that.[/QUOTE]
 OK, sorry, cant find it! Im doing something wrong! There is nothing to do with settings under the help thing or any other option that i can see! 

When im looking at the screen it has one white line at the top and the title of the file is in it! The commands are at the bottom and the main screen is blank! I see no info anywhere about what you said! 

Sorry again for the stupid questions!

EDIT:

Got it now! Thanks for your help! Had to browse through the directories to see the files though! w00t! 

Thanks again!

---

### Post by kevinatkins on 2004-12-23
hi,

i'm having exactly the same problems trying to set up my father's machine with a 19" TFT and Radeon 9200 graphics card - and I'm not a complete newbie!! i'm working on this and hope to post back with positive results soon...

but, in the meantime, in case it helps anyone else, and from experience with other distros

if you've got a monitor for which you don't know the specs. you need to set things up as basic as possible - eg, VGA resolution. it'll probably look horrid, but at least you'll have a workable base from which to improve matters (blanks screens can be a bit worrying!)

to do this -

first, start ubuntu in 'recovery' mode. you'll end up at a command prompt.

next, change to the /usr/bin/X11 directory (cd /usr/bin/X11)

in there, you should find a file called xf86config. (you can check the contents of the directory by typing 'ls', or 'ls | more' if it spills past one screen - the | character is next to the left-hand shift key on a UK keyboard, above \) run it by typing ./xf86config (that's 'dot-forward slash')

you'll be asked a number of questions - it's fairly well documented as you run it. if unsure, answer 'no' or just press 'enter'. when it comes to monitor horizontal and vertical frequencies, go for the 'lowest common denominator'.. finally, when the program finishes, it will write a file called XF86Config to the /etc/X11 directory. 

change to the /etc/X11 directory

check the contents ('ls') - you should see XF86Config and XF86Config-4. You need to back up the original copy of XF86Config-4 by typing 'cp XF86Config-4 XF86Config-4.old', then copy XF86Config to XF86Config-4 by typing 'cp XF86Config XF86Config-4'

Now you can test things - type 'init 2' to go into graphical mode. if all is well, you should end up at a graphical login (probably with very large characters if you've gone for VGA resolution!!)

Hope this helps - it's worked for me before... but I seem to be having more serious problems...

---

### Post by se5a on 2004-12-28
I am having the same problem BUT this is what seems to be happening:

I have an old HP pavilion wich had an onboard graphics card, since then I have installed a PCI Gforce 2 in it as well. 

Now it goes through the setup ok, then hits the unbuntu login (or something cant be sure its to fast) and the screen goes blank.
 
I checked the config file, and to my suprise the screen is corect, it even had the right model number and everything. then I noticed that the graphics device was the ONBOARD graphics adapter, NOT the Gforce 2!
I tryed switching the monitor over, the monitor stayed blank as it went through the setup, but when it got to the ubuntu login the power light on the monitor went from orange to green... but stayed blank.
I tryed haveing a monitor pluged into both 'cards' - no go. 

what can I do? 
other than ripping the Gforce 2 out - its damn cramped inside there, and since it still doesent work when I have the monitor in the onboard one anyway I dont think it is going to solve the problem.

should I edit it to show the Gforce2? if so what do I need to put in there?

I am having a problem with the NIC to (or am going to) but that is for another thread and after I have a chance to play around with it once I can boot...

just found and read this: [http://www.ubuntuforums.org/showthread.php?t=2223&highlight=graphics+cards](http://www.ubuntuforums.org/showthread.php?t=2223&highlight=graphics+cards)
problem is there does not seem to be an option in the bios to disable in onboard one.

---

### Post by Rancoras on 2004-12-28
[QUOTE=se5a]I am having the same problem BUT this is what seems to be happening:

I have an old HP pavilion wich had an onboard graphics card, since then I have installed a PCI Gforce 2 in it as well. 

Now it goes through the setup ok, then hits the unbuntu login (or something cant be sure its to fast) and the screen goes blank.
 
I checked the config file, and to my suprise the screen is corect, it even had the right model number and everything. then I noticed that the graphics device was the ONBOARD graphics adapter, NOT the Gforce 2!
I tryed switching the monitor over, the monitor stayed blank as it went through the setup, but when it got to the ubuntu login the power light on the monitor went from orange to green... but stayed blank.
I tryed haveing a monitor pluged into both 'cards' - no go. 

what can I do? 
other than ripping the Gforce 2 out - its damn cramped inside there, and since it still doesent work when I have the monitor in the onboard one anyway I dont think it is going to solve the problem.

should I edit it to show the Gforce2? if so what do I need to put in there?

I am having a problem with the NIC to (or am going to) but that is for another thread and after I have a chance to play around with it once I can boot...

just found and read this: [http://www.ubuntuforums.org/showthread.php?t=2223&highlight=graphics+cards](http://www.ubuntuforums.org/showthread.php?t=2223&highlight=graphics+cards)
problem is there does not seem to be an option in the bios to disable in onboard one.[/QUOTE]

Sounds like your display adapters are fighting each other.  Is the onboard one disabled in your BIOS?

---

### Post by se5a on 2004-12-28
[QUOTE=se5a]
problem is there does not seem to be an option in the bios to disable in onboard one.[/QUOTE]

there is an option to chose the PCI as the primary but that is it, and it is not working, as it was already selected.
it is getting frustrating.

I tryed the xf86config thingy which half worked, now I get an error telling me that it cant start the X server

somone sugested that there may be jumpers on the mobo but I cant see anything, I dont have the manual, and I have searched the web and cant find anything for a pavilion 6700. I didint have any problems with the screen under mandrake or DSL.

---

### Post by Rancoras on 2004-12-28
Without knowing more about your machine, I'm sorry I can't help.

---

### Post by abstractism on 2004-12-29
heya rancoras, I finally got around to making ubuntu work, I did the xf86 reconfigure, but its not using all of my monitor's screen area, how can I change this? 
thanks :)
abstractism

---

### Post by Rancoras on 2004-12-29
[QUOTE=abstractism]heya rancoras, I finally got around to making ubuntu work, I did the xf86 reconfigure, but its not using all of my monitor's screen area, how can I change this? 
thanks :)
abstractism[/QUOTE]

I would start by adjusting the controls on the monitor itself.  If that doesn't work, I would fall back on the old faithful of making sure that the settings in your X config file match the specs from the manufacturer of your monitor.  It hasn't failed me yet.  :)

---

### Post by abstractism on 2004-12-29
good point ;)
how do I change the xconfig settings? I think its on 1600x1200 and thats too large of a resolution for me, I like 1280x1024

---

### Post by Rancoras on 2004-12-29
I explained how to do that earlier in this thread.  Modify the process as needed for you setup.  All you need is a working text editor.

---

### Post by abstractism on 2004-12-29
oops, sorry

---

### Post by abstractism on 2004-12-29
actually, are you using AIM or yahoo or anything right now? I found the screen section of xf86config-4 but I'm not sure what to do. thanks.

---

### Post by Rancoras on 2004-12-29
Look for the HorizSync and VertRefresh settings and make sure they match the specs provided by your monitor manufacturer.

---

### Post by abstractism on 2004-12-30
I'm getting the xRandR errors, I checked out the other threads and didn't see any fixes..

---


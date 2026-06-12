---
title: "I'm afraid to try the upgrade"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by de Bacon on 2010-05-07
Been strictly an 8.04 user since summer 08.  I have always had problems with the nvidia graphics card (gforce 6600 LE).  Every time I have tried to use the nvidia driver package by clicking the enable "NVIDIA accelerated graphics driver (latest cards)" box, I completely loose my GUI (causing to totally reload the system).  When the latest supposed update came out, (last fall I think) said to resolve that issue, I was afraid to even try it!  I realize this video card is a problem with linux but it has worked with big limits, and I don't need much from a video card.  Ignorance is problematic at times.  I tried to get a new card a month ago, was so fixated on the compatablility with linux issue I purchased a card that wasn't compatable with my mother board, DUH.  

Having an extra HDD on my machine, I decided to test lucid. I disconnected all the others the other day and loaded lucid on that clean disk.  I ended up with no GUI there, so deleted it.  Thus I am still afraid to go through the upgrade process.  

Does anyone know anything about this issue?  I would really like to upgrade to lucid but man it is a nightmare to reload the entire system if it fails.  

Thanks in advance!

---

### Post by zvacet on 2010-05-07
I don´t know the answer,bit it will help if you type in terminal

```
lspci | grep VGA
```

and post output here.Probably somebody else have same graphic card,and that person can help you.

---

### Post by de Bacon on 2010-05-07
The output from command
lspci | grep VGA
is:
05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 LE] (rev a2)

Thanks for thinking about it!

---

### Post by ronparent on 2010-05-07
You actually have the ideal setup for debugging your install!

By booting to the drive you have the 10.04 install on, you can edit the linux kernel boot parameters and reboot until you have pinned down the trouble point. Don't worry about the other disk at this point because if you use bios to select the boot drive they will be unaffected. Because you installed it in isolation from your other OS's (probably a wise move at this point) you have to hold down the left shift to bring up the grub2 boot menu. Hit 'e' on the boot selection and move your cursor down to the linux kernel line.

Your best first bet is to hit <end> and backspace over the quiet splash parameters. This will allow you to see the boot process scroll the screen as you boot. By observing where the boot process hangs up you get some notion of what the problem might be. For instance, if it stalls early, you might try adding one or more of the **noapci noapic nolapic** to the boot line (keep removing **quiet splash** until your system boots). Each time you get further into the boot process, keep whatever works and keep working down the list of f6 options on the live cd until you hopefully find the right combination which permits your system to boot.

Other considerations: Some systems won't boot if you are using two monitors. You may have to try disconnection each one to see which one applies. If you have edd memory you will have to include **edd=on** (check, I may not be remembering correct syntax). You may have to use **nodmraid** whether or not you are using fakeraid (though this may be fixed). If the problem is with your display, **nomodeset** or a number of variation you will have to research. If the problem is fixed by a combination of parameters but occurs again after you allow a boot with **quiet splash**, splash itself may be a problem. This list may not be comprehensive enough, but, others may contribute solutions if you post your progress here. 

If you haven't already noticed, the edits to the grub boot line are effective only for that boot and have to be redited for each boot. Once you have determined your necessary boot parameters you can make them permanent by editing the grub default boot line (**sudo gedit /etc/default/grub**). This may sound daunting but it a sample of what is required to get some systems up and running - except for the many lucky people who have installs work on the 1st try with no fiddling. I hope you give it a run and keep the community informed of you progress. Good luck):P

---

### Post by de Bacon on 2010-05-07
ronparent,
I printed out what you wrote and will proceed with what you suggest.  That list under the F6 command when booting to the live disk could just as well be 1, 2, 3, 4... etc to me, as I have no idea what any of it represents.  

I deleted the load of lucid so will have to open the box and fiddle before I get started.  I do thank you for the effort and shall report on progress and the final outcome as I go along.  
I think I understand all you say above, can only try then try some more.  I am not very knowledgeable about this stuff, no education on it at all but lots of time to fool with it and enjoy the learning curve.

:)

---

### Post by de Bacon on 2010-05-07
I learned something already!  Running from the live cd now.

I was able to load the live CD and having a GUI by marking only **nomodeset**.  Having no understanding of what the words in that menu mean, the last time I did this, I went to the live cd I checked them all and got a GUI.  This is progress.  

I will now load to that clean HDD from directly from here and see if I get a GUI after reboot.  If not I will go through the procedures stated above.  I am sure it will work.  

Another question:  If I get a GUI after a reboot, what does that mean about updating the system I wish to keep on that other disk?  

Thanks,  away I go  try try again.

---

### Post by de Bacon on 2010-05-07
Reporting back,
Same thing, got the system load done, asked to reboot. -> ok 
Then a screen full of messages scroll and on past a full screen with messages like this:

[ 1718.782319 ] end_request: I/O error, dev sr0, Sector 466500

through

[ 1718.861020 ] end_request: I/O error, dev sr0, sector 466556

I don't know what any of that means and there were many lines of that beyond my screen limit with no way to scroll up to see where it started!

Then I reboot.  again, no GUI.

I did as I what I understood of ronparent's instruction, holding the left shift key at boot got to the menu but then my eyes go blurry to what I see because it doesn't make any sense to an untrained idiot like me.  I couldn't make anything happen there.  I tried to find commands but nothing in that language means anything to me, nor could I figure where to even put a command in were I to know the one to enter there.

So I still have nothing on this, well I can get the live cd to work easier now, that is all.  

Experience does tell me that the video card is the issue, though I am only
thinking that due to how 8.04 worked, but I was able to get 8.04 to work by using the live cd F4 command about special video something (can't remember the syntax of that, sorry).

I have time and am willing so onward.  I hope answers or potentials are forthcoming. 

thanks,

---

### Post by ronparent on 2010-05-07
Your making progress and from what you said before you may have the needed boot parameter. 

When you get the boot manu up, hit 'e' to edit the boot line. The boot commands actually occupy several lines. Use the down arrow to navigate down to the linux kernel boot instructions. Hit the <end> key to navigate to the end of the line. Use backspace to delete the **quiet splash** and as you indicated before add **nomodeset** to the end of the line and <ctrl>x to boot. If this works you have it. If everything is working you can mke it permanent by editing the /etc/default/grub file to add the **nomodeset** to the kernel boot line as I instructed before. If not you can systematically investigate the usefulness of some of the other boot parameters. You seem to be making progress.

---

### Post by vwbug on 2010-05-07
Bacon,

Hope you don't have the problems I did. Lost the panel, couldn't right click on the desktop, and files on the desktop didn't show up. It was something with the NVIDIA drivers.  Without the NVIDIA drives those problems went away but I couldn't get my screen to look right with out them. Went back to 9.10, it works fine! Hardy was a good one. I would still be using it if I could have gotten the version of VLC that I wanted.

---

### Post by de Bacon on 2010-05-07
ronparent,
I went back, then understood what you wrote the first time (rolling eyes) Dyslexic here.  I have no idea where it stopped though.  The screen doesn't stay up long enough for me to read even one line.  I didn't think to add nomodeset to that, thinking that it was there from when I sellected it at install.  More time to play though.  Thanks for all the help.  I am sure this will happen.  seems like rocket science to me but I know better.

---

### Post by ronparent on 2010-05-07
Unfortunately, although you installed with nomodeset, that parameter was not tranfered to the install - as I have found out the hard way. My bad - I forgot to mention that:rolleyes:.

---

### Post by de Bacon on 2010-05-07
Okay, entering **nomodeset** into that boot worked.  

I am quite unsure of the format or the location for putting the command line for nomodeset into the **grub** file.  I have it open in a text editor now.  I don't think I would want to delete/remove the statement "quiet splash" there?  
currently the file looks like this:

*****************************
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

**************************************

And so after completing this step, (entering the line in the file) if it works, I would then want to do an update on my other system.  So after completion, would I have the same situation with the same remady, all things equal, of course?  

Progress is being made. I really like the assistance. :) Yet my original question has not been answered.  I have been waiting hours now and nobody is seeming to pick up the thread to help take me to completion in the process.

---

### Post by ronparent on 2010-05-09
Sorry I had overlooked your basic question. The common concensus seems to be that it is not worth the effort to try an 8.04 to 10.04. That you are probably better off doing a clean install. If you have a lot of histiry (ie files) you want to retain, then you might consider putting the 8.04 /home in its own partition - [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

You wouldn't have to endanger the 8.04 install just yet by overwritting it. You could install the 10.04 on the second disk like yoou are doing and designate the separate 8.04 home as your /home target without reformatting it. Or more conservative complete the 10.04 install on your separate disk.  Then after everything is working, you could then 'adopt' (take ownership) the 8.04 /home by the 10.04 install. Although your data would be intact you probably would not be able to access from the 8.04 install thereafter.

---

### Post by nikefalcon on 2010-05-09
> **de Bacon said:**
> 
Having an extra HDD on my machine, I decided to test lucid. I disconnected all the others the other day and loaded lucid on that clean disk.  I ended up with no GUI there, so deleted it.  Thus I am still afraid to go through the upgrade process.  


Does your screen go blank after the bootsplash??
you might want to try reading through these:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

[https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/566379](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/566379) (bug report on launchpad)

---

### Post by de Bacon on 2010-05-09
Last night I arrived at the conclusion for myself that it would probably not work well to got 8.04 to 10.04 all by myself, after kooking through some info about doing an upgrade and unsuccessfully getting it to even start.  So I am oh half way through getting my fresh install rebuilt.  I have quite an assortment of packages installed on 8.04. I am finding most of them  (rolling eyes)  I will have to check out adding some third party repositories, but not there yet. 

I simply don't like to change what works, but...  

I'll get the fresh install done then delete the old one most likely.  I have a good method of keeping my personal data separated from the OS so there is no real problem with that issue. The only big deal is finding all the packages and installing them.  I hope none of my keepers are oblolete!

thanks

---


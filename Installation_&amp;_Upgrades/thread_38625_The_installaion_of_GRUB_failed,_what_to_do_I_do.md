---
title: "The installaion of GRUB failed, what to do I do?"
date: 2005-06-01
forum: Installation &amp; Upgrades
---

### Post by saintsel on 2005-06-01
I'm trying to install ubuntu right now. But i never felt so stupid and helpless in my entire life. I did try to follow the "WindowsDualBootHowTo", but when I came to the the with GRUB i got a failure. It could be beause i wasn't 100 % sure about what partition it should be installed to. What do i do know? I'm not able to try installing GRUB again. I did try to go back a few steps and to see if I was able to restart the GRUB process, but all I get when I try to enter a installation step is "Installation step failed". And what probably made the situation worse is that I did go into the partition step, and I thougt that I could restart the installation process from here. So I startet the partition/formating process again, but of course that didn't help at all. Oh, I feel stupid! Guess many of you get a good laugh know, but I really need help. Don't know what's best to do. 

Is it possible to just finish the pocess now, which I know will not make a good result, reboot with the ubuntu CD and then start the installation process over again? Or is there any other possibilites? I think it's best if I don't touch my computer befor anyone who knows better hopefully comes with a tip or two.  :wink: 

By the way, i didn't touch the MBR. I tried to install GRUB to (hda0,2) based on the following info from QTParted (knoppix live CD): my ext3 partition is on hda3. But the partition tool in the isntaller told med that it had number #4. And that confused me. 

Could someone please help me?

---

### Post by mingus on 2005-06-01
Goodness, don't be so hard on yourself . . . it's just a learning thing.

First, just to be clear . . .

You have one drive with Windows already installed, and you want to install Unbuntu in the remaining space, and then dual boot?

What version of Windows?

Did you ask the Ubuntu install partitioner to move or resize or in any way change your Windows partition?

Did you let the installer automatically set up the partitioning, or did you do it manually?  What are the partitions that were created *and* their mount points?

Did you complete the partitioning and formatting step without any problem, before getting to the boot loader?

And yes, you can re-run the installation from the CD, either using the partitions already created (assuming they were) or destroying and rebuilding the partitions.  

But before you do that, bounce back with the above answers and we can help you to be better prepared.  In particular, if you want to use GRUB and want to protect the MBR for now, that can be a bit tricky, and you may want to use LILO instead.  I'll explain in the next reply.

---

### Post by saintsel on 2005-06-01
He He. Not easy to stay calm when I'm sitting here studing for exams meanwhile installing Ubuntu for the first time :)

I've tried to install one more time and installed GRUB on (hd0,3). That worked. For a while... 
Here's what I've done so far:

I want to dual-boot with XP, so I shrinked the XP partition (NTSF) and made a primary ext3 partition for Ubuntu, and two logical partitions for swap (Linux swap) and shared data(FAT32). I also have a hidden Dell partition. This was done with partition magic 8 and with no errors.

When I came to the partition section in the install I selected ext3 to be bootable, instead of the NTSF partition, and gave it mountpoint"/". The mountpoint for the FAT32 partition was set to "/datashare". (Since my last install went wrong, i also set the installer to format the partitions.) No errors. Then I came to GRUB, selected the GRUB to be installed on (hd0,3) and rebooted the machine. A menu of 4 choises the came ut. 1 choise for starting XP. The 3 others I don't remember exactly. (I think one was called ubuntu recovery). I selected the first choise: Ubuntu (...and some numbers). Then it started to install packages. This went on for about 5 minutes. Suddenly I heard a strange sound, and the screen went black.

I don't know exactly where the install went wrong because I didn't look at the screen when it happend. But before this I noticed some errors saying that there was something wrong about the deafult config file, but I didn't see any errors except from that. So that where I am right know. A black screen...

I tested the CD with Jigdo before I started the install, so I don't think there something wrong with the CD.

Any clue about where I did go wrong?

My XP i still working. Does this confirm that the GRUB is correctly installed?

---

### Post by saintsel on 2005-06-01
I tested to just hit <return> from where I was (the black screen described above) to check if there was any response at all. And there was! A sound. Some kind of drums maybe. The same sound I heard just before I realised the the screen had gone black. So mabye I just don't have a picture, but the install was sort of okey?

Edit: 
For a second I was able to see where Ubuntu went black (by accidently holding in the power off button for a second!). It was waiting for input at user login. Maybe I choosed something wrong when I choosed screen resolutions. Are there any possibilites to change those settings without installing Ubuntu from the beginning?

---

### Post by mingus on 2005-06-01
Yes, it does sound like the install process finished, although something may still have gone wrong with the second stage unpacking.  And yes, it does appear that GRUB got installed OK.

The little drum noise you heard is given by Ubuntu just as gdm (the Gnome X-server startup manager) displays the log-on splash screen.  Get back to this point and hit Ctrl-Alt-Backspace; this should kill the X-server and return you to a shell prompt.

Is your computer a laptop?  It is not uncommon to have problems with the X-server video configuration with a laptop.

Also, how old is this machine?

You might try to following, although this may not work if the X-server config file has the wrong setup:

At the GRUB boot prompt, press 'e' to enable you to add kernel arguments.  Add to the boot line:
noacpi acpi=off vga=normal
and then boot.

---

### Post by saintsel on 2005-06-01
Thanks for your help. Seems that you know what could cause the problem :) But there's still no difference. I boot with the "noacpi acpi=off vga=normal" and there's no change; a black screen. Then i press Ctrl-Alt-Backspace and I can see a shell promt that says: "<host-name> login:". And then it goes black again after 0.5 seconds. When i press the power button to shutdown the computer, I can see the promt for about 3-4 seconds. 

During startup, one sequense seems to fail. I can't see exactly what it is, becuase it scrolls so fast out of the screen, but i think it's about synchronizing a clock. During installation i also skipped the network part, because I use wireless and figured out that it had to wait after the installation. 

Yes, it's a laptop. A Dell Inspiron 2200. Only a week old.

---

### Post by mingus on 2005-06-01
Hmm . . . I can only start guessing now.

What is very strange is your screen going black after you kill the X-server and are returned to the prompt.

If you were at this point OK in the shell and could log-on and use commands, then that would point to a problem with the X-server.  However, if you are sure that the prompt is gone and the system dead at that point, then something is going wrong before the X-server is started.

Re-reading your first post, after you completed the first stage of the install, did you re-boot as instructed and complete the second stage?  If you did not, then there are a lot of packages that did not get installed.

I believe there may be a way to get all of these programs using apt-get or dkpg, but I am new to Debian which has its own unique way of installing.  Someone else would have to help you with the commands to use, or you may find them searching the forums.  It may be simpler/faster for you to just re-install, especially now that you have a handle on the partitioning and boot loader stuff.  If you re-install, be sure to watch the process closely to record any errors.

Sorry I'm not more help.

BTW, the 4 second pause is simply what's called a "soft shutdown", set in the BIOS.  It prevents accidentally killing the system by touching the power button.

---

### Post by saintsel on 2005-06-01
With hitting ctrl+alt+f1 I'm now in textmode. I've seen some other posts about Intel Chipsets and troubles connected with these. So I'll try search the forum for some help.

---

### Post by mingus on 2005-06-01
If after all you can get into a shell, the system is not dead.  That points to the X-server. 

at the prompt, try:

#startx

or 

#gdm

if X does not start, it should give you error messages why.  If nothing happens at all, then it may have not installed properly (again, are you confident the install process stage 2 completed?).  X can be reinstalled, as can gdm.  But if you just did a fresh install and are unfamiliar as yet with apt-get and packages, it would be safer to re-install.

---

### Post by mingus on 2005-06-01
forgot . . . you may need to do this as root.  Depending on how you did your install set up, you will need to either:

1.  #sudo startx
2.  #su
       supply root password
3.  #login prompt> root
                               password

---

### Post by saintsel on 2005-06-01
I get this error when typing "startx":

"Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again"

When typing "sudo gmd":
"gdm is already running. Aborting!"

Does this tell you anythig?

---

### Post by mingus on 2005-06-01
The problem appears to be with either gdm or more likely, the X-server.  You can search the forums, there are many threads dealing with X related problems.  It will be a bit painful, especially if you are new to this.

A few things I would try:

Kill gdm, the X-server, and restart it:
#sudo killall gdm && gdm
#Ctrl-Alt-Backspace
#startx
if it doesn't start, the error message may give me a clue

Force the X package to be reconfigured:
kill as above, then
#sudo dkpg-reconfigure xserver-xorg
#startx

If this hasn't worked, then I would consider that the package may have been broken during my initial installation that did not go well.  Since I haven't used Ubuntu yet, I would then just repeat the installation.

If that did not work, then I would use apt-get to reinstall the X-server, which would insure I got the most recent package, too.  You need to be connected to the Net to do this.

#sudo apt-get update
#sudo apt-get --reinstall install xserver-xorg

If that chokes, then try to remove it and install a new one:
#sudo apt-get update
#sudo apt-get remove xserver-xorg
#sudo apt-get install xserver-xorg

One other alternative is rather drastic.  There is another X-server (Xfree86, Ubuntu's default is Xorg) that you could try installing. 

#sudo apt-get install xserver-xfree86
The package is described at   [http://packages.ubuntu.com/hoary/x11/xserver-xfree86](http://packages.ubuntu.com/hoary/x11/xserver-xfree86)
there are four other packages there that you will want to also install

If none of the above works, you are at a cross-roads.  There can be other problems not yet detected such as hardware related, etc.  You will need to get more help then.

Good luck.

---

### Post by mingus on 2005-06-01
oops . . . left out two lines -

if you do try to switch to xfree86, then be sure to remove xorg first, using the command above, so:
#apt-get update
#apt-get remove xserver-xorg
#apt-get install xserver-xfree86

---

### Post by saintsel on 2005-06-02
For the moment I'm not connected to the Net so I am only able to check out the first tips you gave me. I didn't sett up the network connection at the installation beacuse I use wireless, but I guess I can connect directly to the router through a cable, and then either manaully configure the network connection (don't know how to do that yet) or just re-install while connected to the router. Anyway, here's what happened when i was typing your commands:

#sudo killall gdm && gdm
It returned "Only roots wants to run gdm"
Tried with not the sudo also because i didn't know if this was an error, but it didn't allow me to do that.
#Ctrl-Alt-Backspace
#startx
Now I hear sounds. Sounds like I'm logging into something. But the screen goes black before I see whats happening. 

#sudo dkpg-reconfigure xserver-xorg
It returns: "sudo: dkpg-reconfigure: command not found"

Seems like there may be something missing? Mayebe I should reinstall and try to set up the network at the same time? Then I could also watch the installatin process of the packages and see if I get any errors I didn't see the first time.

---

### Post by mingus on 2005-06-02
Sorry, that was my typo bad - it's *dpkg* - you can try this again, this command reconfigures the package, in this case, tries to re-set up the X-server.

From an earlier post:

*"Re-reading your first post, after you completed the first stage of the install, did you re-boot as instructed and complete the second stage? If you did not, then there are a lot of packages that did not get installed."*

You will know if you completed the second stage.  It will have asked you for your time zone, set up the ordinary user, and *also completed the package installation.*

Consult:
[http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch07s02.html](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch07s02.html)

Since you have a wireless card and the network was not yet set up at this point in the install, I wonder if you pointed apt-get (the package installer) to the right package source, which in your case *at this time* would be the CD.  You cannot use http or ftp because you're not connected to the Net.  In a laptop I installed with a wireless card not yet configured, out of habit I made the mistake of pointing to http and as a result some packages did not get installed and setup correctly.  I had to re-install.

Now, you can repeat this second-stage step now, or just go back thru the whole install.  

Re-running the second stage requires root.  You can try:

#sudo base-config
>password      (this is your user password)  

If sudo doesn't work, and in the install you set up a root password, you can do:

#su
>root password    (note: root, not user)

If you didn't set up root, then try
#passwd root
you will be asked for your user sudo password, and then prompted for a new root password.  After doing this, just do
#su
and you will be in as root, and then you can do
#base-config

Base-config looks just a bit different when run after the install process.  After you point apt-get at the package source you will be dropped into aptitude, a terminal mode package manager.  It's self-explanatory.

Bottom line, you need first to be sure you got all packages installed.  Second, that any necessary updates have been installed.  Third, that the packages were configured correctly, or if there was a failure to install, reinstalled (this can happen for example if the network connection is down and the sources are not available).

Earlier posts have provided all the command to do the above.

Or simply re-install from scratch.

---

### Post by saintsel on 2005-06-02
Thank you very much for your help. But I'm sorry to say that I have to put this away for some days. Maybe even longer, because I'm moving this weekend and I don't know how the network possibilites will be after that. But I really appreciated your willingness to help. And I'm determined that I will get Ubuntu up and going in not too long!

---

### Post by mingus on 2005-06-02
best of luck . . .  :smile:

---

### Post by jonrkc on 2005-06-08
I can't give you detailed help, and besides it looks like others here have done a wonderful job of supplying help for your next attempt.

I thought, though, that you might want to remind yourself that Grub numbers drives one number less, so to speak, than you ordinarily refer to them when operating a system.  In other words, /dev/hda is (hd0) to Grub (with a equivalent to "1") and /dev/hda1 is, to Grub, (hd0,0).  /dev/hda5 would be (hd0,4) to Grub (not that you're likely ever to use that number with Grub).  Some commands with Grub can use either kind of notation.  Grub-reinstall can understand either /dev/hda or (hd0).  When you use Grub's notation, you use the () parentheses.  

Not really a step toward solving your problem, probably, but a useful thing to remember...

By the way, I'm locked out of my OWN installation as normal user at the moment, and I don't seem to have done anything to deserve it!  Luckily I can still get into X via the gdm command as root, and once in X I'm the normal user, thanks to Ubuntu's safeguard against root login to X.  But I can't issue startx as normal user, and that means I can't do customized things safely.  Have spent the last hour and a half searching Google with negative results. 

Good luck with your project!

---


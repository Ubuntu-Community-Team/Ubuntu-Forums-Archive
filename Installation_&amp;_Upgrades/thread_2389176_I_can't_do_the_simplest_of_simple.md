---
title: "I can't do the simplest of simple"
date: 2018-04-12
forum: Installation &amp; Upgrades
---

### Post by john_fox on 2018-04-12
I just upgraded from 14.4 to 16.4 
I get the login prompt
I enter the computer name
I get the password request 
I enter the password
it tells me my last login attempt time and date
then it gives me the computer name and model with a $ and blinking dash
PROBLEM I can't remember what to enter now to get it to boot up to firefox and online?
I know it's something simple but at my age I am deep into CRS and could use some kind help please.

---

### Post by ubfan1 on 2018-04-12
Can you successfully log into the guest session?  If so, your home directory probably has some leftover config files (the files/directories starting with a dot, and are "hidden" in most directory listings.  At the $ prompt,can you type in terminal commands like
ls
and see files you expect in your home directory?  
Do you have video hardware requiring a proprietary driver (like Nvidia,...)?  Maybe the driver needs to be reinstalled.  If you type "e" on the grub menu screen to edit the boot commands (instructions at bottom of screen), and enter "nomodeset" at the "quiet splash" words on the line starting with "linux", does that allow your desktop to show?

---

### Post by john_fox on 2018-04-12
when I type in ls on the command line  a listing of folders that I recognise show up, some are blue colour and some are white.
no Nvidia.   what to do now?
and thanks for your help

---

### Post by yancek on 2018-04-12
After logging in with your user name ahd password, have you tried typing in startx, hit the Enter key?  What happens?

---

### Post by ubfan1 on 2018-04-13
Your login works, but the X server is not running, probably crashed (see /var/log/Xorg.0.log for a reason, but it may not mean much to you).
Typing startx should start the X server, but it probably will just crash again.
  The most likely causes are:
 1) Leftover dot files in your home directory (confirm this with a working login to the guest session) .
   Solution, move several directories/files to another directory:
    From the black screen with a cursor, your current working directory is your home directory.
    mkdir saved
    mv .Xauthority saved
    mv .cache  saved
    mv .local    saved
    mv .config  saved
Then try startx,  and if that works, things should be working again.
Or
2) You have a video driver problem.  See askubuntu.com for "login loop" problems, but basically, edit the grub menu by typing "e" (instructions at bottom of screen), then adding
the word "nomodeset" next to the words "quiet splash" on the line beginning with "linux".  Boot with ctrl-x or F10, and if that works, run "Software and Updates" and under the "Additional Drivers" tab, select the "tested" Nvidia driver, for example.

---

### Post by john_fox on 2018-04-13
thank you ubfan1,
I tried typing startx and you were right,  unable to connect to x server connection refused
I can't confirm leftover dot files I don't even know how to log in to guest session? [I'm so bad]
I tried entering mkdir saved,mv Xauthority saved etc.etc.etc.    nothing
I will look at video driver at askubuntu .com login loop and see what happens?
again thanks ubfan1 for your help and patience.  john

---

### Post by ubfan1 on 2018-04-13
At the login prompt, you should have your username, and below it, a "Guest Session".  Select the guest session, no password, and see if that gets you to a desktop.

When you tried the mv commands, all the files to move start with a dot -- you did type the dot didn't you?
You can list all files, even the ones stating with a dot with the -A switch on the ls command:  ls -A
There are many of them, but I think the ones causing trouble are the ones I previously listed.

---

### Post by john_fox on 2018-04-13
I don't get a guest session option at the prompt what I get is
ubuntu 16.04.4 lts john-extensa-5620 ttyl              below that I get
john-extensa-5620 login:       no option for guest session
I log in with john it then asks for password:
when I enter the password it gives me a disclaimer no warranty 
then it gives me 
john@john-extensa-5620:~$ and a prompt 

is any of this helpful?

---

### Post by ubfan1 on 2018-04-13
I thought 16.04 added the guest session, but maybe it's the unity interface,or maybe your system is not fully upgraded.  If you are not running unity maybe that explains the missing guest session.  But it wouldn't hurt to try an update at the prompt:
sudo apt-get update
sudo apt-get install
and see if things change.
For the video hardware, please run 
lshw -c video
and post the results here.

---

### Post by john_fox on 2018-04-13
ok after entering sudo apt-get install i get....
err:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial inrelease    could not resolve 'us.archive.ubuntu.com
err:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise inrelease   could not resolve
err:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-security inrelease   could not resolve
err:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates inrelease    could not resolve
err:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports inrelease     could not resolve
reading package lists...done
w: no sandbox user '_apt' on the system, can not drop privileges
then it says failed to fetch each of the listed err 1 through 5
w: some index files failed to download. they have been ignored or old ones used instead
any help?

---

### Post by QIII on 2018-04-13
Hello!

Would you please copy and paste the entire thing from your initial command to the end of the full response instead of inserting "and then I got ...".

You may be leaving out important details.  Please enclose the text in code tags to preserve formatting.

---

### Post by john_fox on 2018-04-13
this computer I'm using now is not the problem computer, the problem computer is my other computer that I can't boot up and so can't copy and paste anything. sorry, I wish I could.
 I'm doing the best I can and do appreciate y'all working with me as best you can.

---

### Post by QIII on 2018-04-13
Where did you get the text that you posted previously?

---

### Post by john_fox on 2018-04-13
I got the text from the other computer.
when I turn it on I get the black screen that says ubuntu 16.04 4 lts john extensa-5620 ttyl
next line down says     john-extensa-5620 login:
when I login it asks for a password when I enter the password it tells me the last time and date I logged in then on the next line down it says
john@john-extensa-5620:~$ and a blinking prompt.
that's as far as it goes until I enter the commands suggested in the other posts.
I cannot open firefox, get online, copy and paste, print or anything else?  yet! but I'm sure we'll be able to work it out, because y'all are awesome!

---

### Post by QIII on 2018-04-13
Can you run those other commands and snap a photo with your phone to post back here?

Details that seem unimportant to you may be critical for diagnosing your issue.

---

### Post by john_fox on 2018-04-13
I haven't thought of that, I'll try and see.
thanks for the idea.

---

### Post by john_fox on 2018-04-14
OK I hope this works, not a good picture because of reflection hopefully it will work.

---

### Post by ubfan1 on 2018-04-14
Looks like you're running the 3.13 kernel from 14.04,so the upgrade didn't seem to complete.  What kernels do you have in /boot? (post the output of ls /boot  ).   If you have a full 4.4 kernel (the abi..., config..., initrd..., vmlinuz... System.map..., update your grub.cfg file by running:
sudo update-grub.   That might be enough to fix X, which was built for 4.4, but you are now running 3.16.  Reboot and check the running kernel with
uname -a
  Think about backups of your files, in case a reinstall becomes necessary.

---

### Post by john_fox on 2018-04-14
this is what I get with: ls /boot
all 3.13
I have all important, to me, back-ups so a reinstall is not a problem.

---

### Post by ubfan1 on 2018-04-15
Oh my, 40+ old 3.x kernels, and none of the 4.4 series.  I think it would take longer to purge those than to just reinstall.  Then you should look into some periodic maintenance procedure to help clean up old kernels.

---

### Post by mörgæs on 2018-04-15
Yes, do a fresh install. Since your hardware is some years old then 16.04.4 will do and it's good through April 2021. 

When the new system is installed you should change all passwords which have been entered. 

Daily routine for keeping the system fit:
```

sudo apt autoremove
sudo apt update
sudo apt dist-upgrade
```

---

### Post by john_fox on 2018-04-15
OK guys, I will attempt a fresh install.
I do want to thank every one for the help.
I have limited internet service so after the storms go past I will download a new copy, saved on this computer till I can burn a cd .
gotta go now storms are heating up.
thanks for now.
john.

---

### Post by mörgæs on 2018-04-15
Good luck with both the storm and the install.
The ISO is too big for a CD. Your options are a USB stick or a DVD.

---

### Post by john_fox on 2018-04-15
dvd yes, I will try to download to this computer then copy to a dvd then load to the acer computer.
thank you all for the kind help for this helpless old man!

---


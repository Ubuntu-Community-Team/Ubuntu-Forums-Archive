---
title: "password asked after upgrade to 11.10"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by pagheca on 2011-10-19
Hi,

I updated to Ubuntu 11.10 today a Dell 9400 Inspiron (dual boot with Windows XP). After the installation was completed and a system restart (without any major error message), I got a screen asking for my password. If I type the right password, I can see some graphic format changes for a fraction of a second (no error messages displayed) and then the password is still requested. I can't go ahead of this. All I can get is a login screen with my username and a password request. I tried to restart again but nothing change.

Note that the password is RIGHT. I'm sure about this because if I type a wrong password the text "Invalid password, please try again" appears in red under my username. If I type the right password this text is not displayed.

thanks for any help

---

### Post by pagheca on 2011-10-19
One more: 

The only option I have is to try to shut down by clicking on the "switch" icon on the right upper corner, but if I try this, the system first asks to choose from restart, cancel and shut dow, then, after I type the password, the login screen appears again. 

The only way to restart is to press the power button for a few seconds but after reboot the same login screen appears again.

---

### Post by youngunix on 2011-10-19
at the log in screen, click the gear icon and select "Ubuntu 2D" then try to log in.

---

### Post by pagheca on 2011-10-19
Thanks - I actually tried all the different options. No differences found.

---

### Post by bock42 on 2011-10-19
Sorry I don't have a solution, but I wanted to add that I am having the same problem.

---

### Post by pagheca on 2011-10-19
you are never alone... Can you please specify your platform details?

---

### Post by bock42 on 2011-10-19
Ubuntu 11.10
Linux 3.0.0-12-generic
x86_64

Running on:
ASUS G53SW laptop
nVIDIA GEFORCE GTX 460
Intel core i7

---

### Post by alphacrucis2 on 2011-10-19
Maybe this:

[http://ubuntuforums.org/showpost.php?p=11359168&postcount=11](http://ubuntuforums.org/showpost.php?p=11359168&postcount=11)

---

### Post by bock42 on 2011-10-19
> **alphacrucis2 said:**
> Maybe this:

[http://ubuntuforums.org/showpost.php?p=11359168&postcount=11](http://ubuntuforums.org/showpost.php?p=11359168&postcount=11)

I tried that, and received the following:

chown: cannot access `/home/andrew/.gvfs': Permission denied

---

### Post by noelc on 2011-10-19
I have exactly the same problem. Cant get passed the user logon screen after upgrade.

Very frustrateing as I dont operate a dual boot (Only Ubuntu). I have tried everything

---

### Post by pagheca on 2011-10-20
[this]("http://ubuntuforums.org/showpost.php?p=11359168&postcount=11") solution worked for me: 

Note that I just used a few lines:

sudo chown $USER:$USER /home/$USER -R
sudo apt-get update && sudo apt-get install --reinstall dpkg
sudo apt-get install --reinstall lightdm unity-greeter
sudo service lightdm stop
sudo service lightdm start

I can't tell if they are all required. 

Note that you can switch to a text terminal by pressing Alt-Ctrl-F1, and return back to the graphic login with Alt-Ctrl-F7.

There are very many other solutions online that seem to work for different users. Search "ubuntu login loop" if this doesn't work for you, and please post the solution you found for the others...

cheers

---

### Post by RitterSport on 2011-10-21
I can't get past the login screen either.  And, when I go to the console, I can't login.  How can I try those steps if I can't get past the login screen?  Is there any way to have lubuntu display the available user IDs?  I know for sure what the password is, but maybe I have the user ID wrong.

Anyway, I'm on an eeepc 701 and I just upgraded to 11.10.

---

### Post by pagheca on 2011-10-21
Can you tell us why you can't login? You get any error message?  Any message at all?

---

### Post by 23dornot23d on 2011-10-21
Check Xauthority in the link at the bottom for failed upgrades there are some solutions .......

---

### Post by RitterSport on 2011-10-21
Login Incorrect, when trying from the console.  From the windows environment, no message.

---

### Post by 23dornot23d on 2011-10-21
Also the link to solution for failed password .... in my footer .... may help


also this one .... [http://ubuntuforums.org/showthread.php?t=1863430](http://ubuntuforums.org/showthread.php?t=1863430)

---

### Post by RitterSport on 2011-10-21
The problem I'm having is that I can't log in at all, in order to try those other solutions.  Until the upgrade, I never had lubuntu ask me for my user ID, so I'll admit that I'm not sure what it is.  I know what the password is, though, since I enter than when doing any sudo stuff.

I'm not all that fantastic at linux, so if these are newbie questions, I apologize.  I just can't figure out how to get past the login.

---

### Post by 23dornot23d on 2011-10-21
When it starts up with Lightdm .... the username should be shown .... 

Which system are you Running Ubuntu 11.10 or something else ?

---

### Post by RitterSport on 2011-10-22
I'm running Lubuntu 11.10.  I don't see any user ids when I reboot, though.  I guess I'm not sure what lightdm is.

---

### Post by RitterSport on 2011-10-22
For what it's worth, when I was upgrading, it asked whether to overwrite 2 or 3 configuration files.  I said OK, and maybe that's why it's asking for a user ID and password on restart.

---

### Post by RitterSport on 2011-10-22
I figured it out.  I booted the eeepc off of an old ubuntu live CD (actually, a USB stick) and used that to figure out my user ID.  Thanks, everyone, for the help, and sorry for the rookie mistake!

RS

---


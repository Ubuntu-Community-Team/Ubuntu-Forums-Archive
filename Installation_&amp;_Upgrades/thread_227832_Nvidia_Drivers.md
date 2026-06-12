---
title: "Nvidia Drivers"
date: 2006-08-02
forum: Installation &amp; Upgrades
---

### Post by abcdef on 2006-08-02
Ok, I have setup Nvidia on a Slackware install before and it worked fine.

But I tired to install the Nvidia drivers on my Ubuntu Hoary Hedgehog install but it doesn't work.

I followed these instructions: [http://ubuntuguide.org/wiki/Ubuntu#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu#How_to_install_Graphics_Driver_.28NVIDIA.29)

I completed up to where it says restart GNOME (Ctrl + Alt + Backspace) and when I did that I just got a blank black screen. Now every time I boot up it happens. 

I have NVidia 6200 AGP graphics card and Ubuntu 5.04.

I have had two ideas on how to temporarily diable NVidia until I can get it working. Thats to run "sudo nvidia-glx-config disable" or restore my backed up xorg.conf. But I cannot get to a shell of any sort. The screen is black and there is nothing I can do.

Can anyone help me A) get it back to what it was before so I can use it again B) get NVidia drivers installed?

Thanks for reading my thread. Ask me for any info you need, I think I have included it all.

---

### Post by Ziox on 2006-08-02
> **abcdef said:**
> Ok, I have setup Nvidia on a Slackware install before and it worked fine.
 
But I tired to install the Nvidia drivers on my Ubuntu Hoary Hedgehog install but it doesn't work.
 
I followed these instructions: [http://ubuntuguide.org/wiki/Ubuntu#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu#How_to_install_Graphics_Driver_.28NVIDIA.29)
 
I completed up to where it says restart GNOME (Ctrl + Alt + Backspace) and when I did that I just got a blank black screen. Now every time I boot up it happens. 
 
I have NVidia 6200 AGP graphics card and Ubuntu 5.04.
 
I have had two ideas on how to temporarily diable NVidia until I can get it working. Thats to run "sudo nvidia-glx-config disable" or restore my backed up xorg.conf. But I cannot get to a shell of any sort. The screen is black and there is nothing I can do.
 
Can anyone help me A) get it back to what it was before so I can use it again B) get NVidia drivers installed?
 
Thanks for reading my thread. Ask me for any info you need, I think I have included it all.
 
Just out of curiosity, why are you running Hoary Hedgehog? The newest version is Dapper Drake (6.06) I suggest you upgrade to it for better driver support.  As for you're problem, do this command and see if you can get your display back:
 
sudo dpkg-rconfigure xserver-xorg
 
and reboot
 
P.S. I hate to say this, but there are tons of threads that have already discussed your kind of problem, so please do a little searching before posting (I know it is easy to "just post", but no one likes to spoon feed anyone). I'm not trying to be harsh, just honest. And If i had insulted you, I'm sorry.

---

### Post by abcdef on 2006-08-02
I know what you mean sorry, I didn't think to search.

I couldn't type in console commands as I did't have access to a console.

I booted RIP (Recovery Is Possible Linux LiveCD) and managed to swap the xorg.conf for the backed up one. Now I don't have a black screen and I can log in as normal.

I don't have Dapper Drake because I'm using an old CD that I got from shipit.ubunu.org, my internet has been too slow to download a new version. Just yesterday my broadband got upgraded to 1meg so I will get the new update ("sudo apt-get dist-upgrade" isn't it?)

Right now I'm doing a software update and when its completed I will update to Dapper Drake. Hopefully then I will be able to sort my NVidia Drivers out properly.

Sorry about asking people to spoonfeed me, I know how annoying it is. I just didn't think.

---

### Post by Ziox on 2006-08-02
> **abcdef said:**
> I know what you mean sorry, I didn't think to search.
 
I couldn't type in console commands as I did't have access to a console.
 
I booted RIP (Recovery Is Possible Linux LiveCD) and managed to swap the xorg.conf for the backed up one. Now I don't have a black screen and I can log in as normal.
 
I don't have Dapper Drake because I'm using an old CD that I got from shipit.ubunu.org, my internet has been too slow to download a new version. Just yesterday my broadband got upgraded to 1meg so I will get the new update ("sudo apt-get dist-upgrade" isn't it?)
 
Right now I'm doing a software update and when its completed I will update to Dapper Drake. Hopefully then I will be able to sort my NVidia Drivers out properly.
 
Sorry about asking people to spoonfeed me, I know how annoying it is. I just didn't think.
 
great! I'm glad that it is working for you now.  As for dapper drake updates, I think the command to upgrade is this:
 
gksu update-manager -d
 
either that or change you sources.list.  Change all hoary instances to dapper...
 
And if you have any problem, search the forum :mrgreen: I'm sure there is a solution already.

---

### Post by abcdef on 2006-08-02
I read somewhere on the forums that its best to go to breezy then to dapper.

I've got it updated to Breezy but my modem doesn't work now :( 

Its a Sagen Fast Eagle modem. I had to compiel the drivers for it before, so I think I have to do it again because its now Breezy.

How would I make sure that the old drivers are gone before I compile the new ones?

---

### Post by abcdef on 2006-08-03
Ok, I'm on Dapper Drake now (I just downloaded the iso and installed it) but my modem doesn't work.

I'm gonna search around to see if someone else has had this issue. If not I'll post a message and pray that someone can help :)

---


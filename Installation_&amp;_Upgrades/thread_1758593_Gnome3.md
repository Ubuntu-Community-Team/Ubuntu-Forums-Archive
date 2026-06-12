---
title: "Gnome3"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by vikrantalmelkar on 2011-05-14
Hi All,

How can I upgrade to Gnome3. I tried using software center, but I am getting an error all the time.

Is there a different way to upgrade the Gnome3

Thanks
Vikrant

---

### Post by akand074 on 2011-05-14
To install:

```
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell gnome-session
```

To remove:

```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:gnome3-team/gnome3
```

In a terminal window

---

### Post by vikrantalmelkar on 2011-05-14
Hi Akand074,

thanks for the code. I followed the steps. but now when i reboot nothing is coming up and ubuntu does not start. 
It stops at checking battery status.

Can you please help me in getting up and running

thanks
Vikrant

---

### Post by kansasnoob on 2011-05-14
You should report him to the moderators because he gave instructions without the prominent warning from the PPA:

> This package contains packages from GNOME3 and their dependencies so they can be used in Ubuntu 11.04 (Natty). This PPA is EXPERIMENTAL and MAY BREAK YOUR SYSTEM. There is no downgrade process.

Source:

[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)

People need to provide adequate warnings about potential breakage!

---

### Post by rootnet47 on 2011-05-14
I've installed gnome3-session from synaptic package manager before some days, but I didn't find any change in "System Monitor"(it is still GNOME 2.32.0). After got this post I tried above cmds but returned that gnome-shell is already updated. I can't understand the mater with not changing the GNOME 2.32.0 figure on "System Monitor".

---

### Post by akand074 on 2011-05-14
> **kansasnoob said:**
> You should report him to the moderators because he gave instructions without the prominent warning from the PPA:



Source:

[https://launchpad.net/~gnome3-team/+archive/gnome3]("https://launchpad.net/%7Egnome3-team/+archive/gnome3")

People need to provide adequate warnings about potential breakage!

Umm, he's asking how to install Gnome 3 in Ubuntu. That's how you do it. I think it goes without saying that it can break your system. Everyone knows that It is all over the place. I also gave him the code to revert it should he want to or if it broke his system. I've successfully installed it AND reverted back several times on several PCs. I think that was uncalled for. 

Edit: Also, to be honest. It's not my responsibility to warn him for something he asked for in particular. It's not like I intentionally gave him malicious code. I just gave him an experimental ppa to use. If he was worried he could have checked the ppa before adding it, or asked if it has possible negative outcomes.

Edit2: As a realization to what may have gone wrong is perhaps he's not running 11.04. I've already helped people, and also read tonnes of threads where people are trying to install Gnome 3, and all of them were in 11.04, some asking if it's possible from 10.10. Point is, when someone asked me how to install Gnome 3, my natural assumptions was a) he was aware it required outside source to install it (as if it was available by default he'd be aware of it) and thus is aware of the risk of using an outside source, and b) he is using 11.04.

I'm rather offended that you'd say I should be reported... I'm a volunteer helper. He asked how to do something I told him. He would have given more detail if he was worried about compatibility/breakage, in which case I would have elaborated.

---

### Post by akand074 on 2011-05-14
> **vikrantalmelkar said:**
> Hi Akand074,

thanks for the code. I followed the steps. but now when i reboot nothing is coming up and ubuntu does not start. 
It stops at checking battery status.

Can you please help me in getting up and running

thanks
Vikrant

Hey, I'm unsure why this is happening. But does the grub menu come up where you choose Ubuntu? If not press/hold shift on startup to force it to come up. Boot into the recovery kernel and go into a shell with networking and login (just type login I believe and it'll ask for username/pass) to your account from there and run the code I gave you to get rid of Gnome 3 and revert you back to your previous settings. From there if you'd like we can try to figure out what went wrong if you still intended to try Gnome 3. It's still experimental in Ubuntu 11.04 but it's hopefully planning to be available working in Ubuntu 11.10.

I just realized, are you not running Ubuntu 11.04? If not that could be the issue! That ppa only supports 11.04 well I believe (maybe 10.10 if I remember correctly, but definitely I'd say you should be in 11.04).

---

### Post by HookedOnLinux on 2011-05-15
akand074.......from your experience with gnome3, is it worth while? How does it perform, stability...etc? and when people say that something can break your system, I'm assuming they're talking about software and not hardware? 

Oh, ignore the other dudes reply about reporting you, if it wasn't for people like you helping others, there would be more people reverting back to windows.
Thanks!

---

### Post by akand074 on 2011-05-15
> **HookedOnLinux said:**
> akand074.......from your experience with gnome3, is it worth while? How does it perform, stability...etc? and when people say that something can break your system, I'm assuming they're talking about software and not hardware? 

Oh, ignore the other dudes reply about reporting you, if it wasn't for people like you helping others, there would be more people reverting back to windows.
Thanks!

Thanks! Personally, I reverted back to Unity for now because Gnome 3 in Ubuntu isn't complete. The screen occasionally gets scratchy and some stuff are still Gnome 2 applications (haven't been updated) and I couldn't get file sharing to work. Basically, it's completely useable, but with minor flaws but doesn't really feel like it's Ubuntu. I personally would wait until 11.10. Ubuntu 11.10 is supposed to be built over Gnome 3 so basically installing gnome-shell would be just a matter of sudo apt-get or software centre. But if you have no problem with minor issues/instability it's still more than useable. Here is a [link]("http://ubuntuforums.org/showthread.php?t=1742343") for common issues/fixes should you decided to stick with it.

And yes they are talking about software of course. Not your hardware.

---

### Post by vikrantalmelkar on 2011-05-15
Hi Akand074,

Firstly thanks so much for replying back so quickly. I am running Ubuntu 11.04. I wanted to upgrade to Gnome 3. but then encountered a problem. After the boot screen, nothing was starting. Tried the code that you gave me to remove gnome3 but i am getting the following error:

sudo ppa-purge - Command not found

what can i do from here?

secondly, forget what the other dude said about reporting. if people like you were not there to help me, i dont know what i would have done. the main reason for me shifting to windows was the help i will be getting from the community and people like yourself.
Keep up the good work and listen to everybody but do what your heart tells you to do

Thanks very much for all your help.

Vikrant

---

### Post by deciding39 on 2011-05-15
sudo apt-get install ppa-purge

...to install ppa-purge. then hopefully that command will work. :)

---

### Post by akand074 on 2011-05-15
> **vikrantalmelkar said:**
> Hi Akand074,

Firstly thanks so much for replying back so quickly. I am running Ubuntu 11.04. I wanted to upgrade to Gnome 3. but then encountered a problem. After the boot screen, nothing was starting. Tried the code that you gave me to remove gnome3 but i am getting the following error:

sudo ppa-purge - Command not found

what can i do from here?

secondly, forget what the other dude said about reporting. if people like you were not there to help me, i dont know what i would have done. the main reason for me shifting to windows was the help i will be getting from the community and people like yourself.
Keep up the good work and listen to everybody but do what your heart tells you to do

Thanks very much for all your help.

Vikrant

Thank you. Yes as the guy has said above

```
sudo apt-get install ppa-purge
```Make sure you have networking. This will install ppa-purge then the command:

```
sudo ppa-purge ppa:gnome3-team/gnome3
```To remove it. Where did you run this code? in the recovery shell? Make sure you select drop to shell with networking to install it!

---

### Post by vikrantalmelkar on 2011-05-16
Hi akand074,
 
I have tried the code you gave me again in "Drop to shell with networking" and it is still giving me that the command is a bad commad. 
 
I guess i will have to reinstall 11.04 again and try upgrading to gnome 3 again.
 
Thanks
Vikrant

---

### Post by akand074 on 2011-05-16
> **vikrantalmelkar said:**
> Hi akand074,
 
I have tried the code you gave me again in "Drop to shell with networking" and it is still giving me that the command is a bad commad. 
 
I guess i will have to reinstall 11.04 again and try upgrading to gnome 3 again.
 
Thanks
Vikrant

Odd. Did you type "login" to login to your account? That may have been necessary. Anyways, I hope it works out better for you next time. [Here's]("http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3") a good source for installing Gnome 3.

---

### Post by akannankeril on 2011-05-28
Hi,

i have had the same issue. installed gnome3 on 11.04, was working OK till i did an update.
ubuntu wont start now, grub is fine when i boot to ubuntu i get the first loading screen n then nothing happens.
boot into recovery mode then select normal mode from drop down list and i get a command promt- to login 
no graphical screen. tried all cmmands, no use. just installed ppa purge as per this thread, it went ok. but when i gave command for removing gnome 3, after a fewseconds, gave something like ppa:gnome3-team not found

please help

---


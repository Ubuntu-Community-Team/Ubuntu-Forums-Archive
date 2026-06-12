---
title: "Upgrading to 10.04"
date: 2009-12-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rossp@purepagesgroup.com on 2009-12-09
Yesterday I noticed on update manager an option to upgrade to 10.04 - ever a fan of trying new things I went for it but it stalled about half way through the installation process and now when I boot up I've lost all gui's and have to login via command line which is ok but then get to the next command and am totally stuck as I don't know many commands for the terminal.

Is my installation broken or can I launch into graphical mode somehow?

Thanks.

---

### Post by coffeecat on 2009-12-09
10.04 is barely in Alpha. The Alpha 1 is due to be released tomorrow. It's probably possible to rescue your installation from the command line but, unless you're willing to put up with potential breakages and problems during the pre-release testing period, you may not want to do this.

But I'm curious about Update Manager offering you a dist-upgrade. Normally, it shouldn't do this. Did you run 'sudo update-manager -d' before this notification came up?

---

### Post by darkod on 2009-12-09
> **coffeecat said:**
> 
But I'm curious about Update Manager offering you a dist-upgrade. Normally, it shouldn't do this. Did you run 'sudo update-manager -d' before this notification came up?

+1
How did you ever get an offer to upgrade to 10.04? Is that a bug that needs to be looked at urgently? If it starts happening and people upgrade by accident all hell will come loose... :)

---

### Post by rossp@purepagesgroup.com on 2009-12-09
I normally check all the boxes on the respository list so I can get the most upto date stuff even if its not fully tested/released yet.

I did look online yesterday and there was nothing on 10.04 at all not even a couple of screen shots.

So I thought what the hell, give it a go.  I don't mind using the command line if I can at some point get back to the graphical interface.

Would be interested in learning how to rescue my installation from here though....

Thanks.

---

### Post by phillw on 2009-12-09
> **rossp@purepagesgroup.com said:**
> I normally check all the boxes on the respository list so I can get the most upto date stuff even if its not fully tested/released yet.

I did look online yesterday and there was nothing on 10.04 at all not even a couple of screen shots.

So I thought what the hell, give it a go.  I don't mind using the command line if I can at some point get back to the graphical interface.

Would be interested in learning how to rescue my installation from here though....

Thanks.

That is *NOT* the way to go a playing with 10.04 (Or any other pre - rc release !!)

But, as you have it - you'd better head over here --> [http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

And get a launchpad account, if you have not already gotten one.

I was not aware of a GUI problem. The only one that I saw was no floppy drive - however 10.04 is the subject of daily builds, so it's quite possible (and likely) that they'll break it now and again ;-)

That said, the alpha is imminent - and usually has a lot of the gremlins sorted.

Regards,

Phill

---

### Post by PaulW21781 on 2009-12-09
Mine was also prompting me about an upgrade to 10.04 when running updatemanager without -d option earlier today.

Just checked now, and it's no longer mentioned or prompted, so I guess there was an issue with the repo's or something...

---

### Post by phillw on 2009-12-09
> **darkod said:**
> +1
How did you ever get an offer to upgrade to 10.04? Is that a bug that needs to be looked at urgently? If it starts happening and people upgrade by accident all hell will come loose... :)

Calm down, darkod - it's only a commercial (UK joke). TBH, with all the 'fun' with grub2 - i think 10.04 will be a walk in the park !!! (SSShhh, don't tell anyone, tho' ;-)  )
I have this horrible, sneaky, growing feeling that 9.10 is, in fact the beta for the 10.04 LTS -- But, that's just IMHO - lol

I couldn't see it under the normal release system from within synaptic - however, of course, it is there in repositiries if you ask for synaptic to go looking in the lucid 10.04 ones for you!!

Phill.

---

### Post by rossp@purepagesgroup.com on 2009-12-09
I'm not worried about using an alpha release as we have 9.10 running on the laptop in the office too and Linux Mint 8 (is that a swear word around there parts?) on the test machine.

I was just wondering if there's a command from the terminal/command line to get the graphical stuff kickstarted?

Thanks.

---

### Post by phillw on 2009-12-09
> **rossp@purepagesgroup.com said:**
> I'm not worried about using an alpha release as we have 9.10 running on the laptop in the office too and Linux Mint 8 (is that a swear word around there parts?) on the test machine.

I was just wondering if there's a command from the terminal/command line to get the graphical stuff kickstarted?

Thanks.

Did you say you were running in a server environment ? in which case, 10.04 won't give you a GUI. Anyways - to get the GUI, follow this thread (The more recent stuff is lower down the page) [http://www.ubuntux.org/how-to-start-the-gui-from-the-prompt-screen](http://www.ubuntux.org/how-to-start-the-gui-from-the-prompt-screen)

Regards,

Phill.

---

### Post by coffeecat on 2009-12-09
> **rossp@purepagesgroup.com said:**
> I normally check all the boxes on the respository list so I can get the most upto date stuff even if its not fully tested/released yet.

Which presumably means you ticked the proposed and backports boxes. Oh dear. If only I had £10 for every time I've posted  this link:

[https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates)

> Enabling the proposed updates repository can break your system. It is not recommended for inexperienced users.Welcome to the world of broken systems. But that still doesn't explain why Update Manager offered a dist-upgrade.

It's possible that you have a broken GUI because the updates available in the Lucid repository were inconsistent while you were trying to do the upgrade. This is [common before release]("http://ubuntuforums.org/showthread.php?t=1343434") and experienced alpha/beta testers know about it. From the console you could try:

```
sudo apt-get update
sudo apt-get upgrade
```... and hope the package archive is now consistent, but if you've been ticking boxes inadvisedly I wonder if there's something else you've forgotten or not told us about.

---


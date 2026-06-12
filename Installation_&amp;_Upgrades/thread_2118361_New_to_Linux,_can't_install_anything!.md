---
title: "New to Linux, can't install anything!"
date: 2013-02-21
forum: Installation &amp; Upgrades
---

### Post by zaospawn on 2013-02-21
To start, I am 100% new to Linux and I am all around technology noob so please be nice and easy on me :) Anyways I have been trying to install Netflix desktop but it says I need Wine (which I have been meaning to get so I can use certain Windows programs) and so when I tried install wine I get this:

> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.5 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.I tried installing wine1.5 and I get this:

> E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?So in brief, I have no idea what I am doing :(
All I want to do is watch Netflix and be able to use some Windows programs. I know I have a huge learning curve and this is a bit of a hot mess issue but are there any kind souls willing to help me out, please?

---

### Post by carl4926 on 2013-02-21
> All I want to do is watch Netflix and be able to use some Windows programs

You sound like a candidate for a Windows OS.

From what I read, it rather sounds like you might be better starting again.

Perhaps too, you could tell us if you used the latest version 12.10? 

Once you are installed, update the system and reboot.

The place to look for software is the Software Centre, but you need to be patient with it, it has the habit of looking like it's not working properly.
Wine can be found in there.

I think at this stage you may struggle though. And I really recommend you stick with Windows and boot to Ubuntu as and when you have time to learn some more, then give yourself 12 months or so of that....

---

### Post by zaospawn on 2013-02-21
It was late at night when I posted this so I apologize for my lack of polish. I am currently using Ubuntu 12.10 through Wubi on my Windows 7. There are other things I want to use Ubuntu for (Python, C++, etc) but at the time I posted this I was frustrated and really did not think through how to articulate myself.

I have done the most recent updates and even set a mirror appropriate for me, however there are still lots of things unavailable from the software center. I found out how to get Netflix-desktop but when I tried doing it through the terminal I got those errors then when I tried installing Wine I got the same thing as well. Every time I try installing things through the terminal I run into several brick walls. **Instead of telling me to quit, could you please offer some solutions or help instead?**

---

### Post by snowpine on 2013-02-21
Welcome to the forums!

I agree with the above that you should definitely keep Windows installed on your machine, perhaps a "dual boot" so you can choose between Ubuntu and Windows each time you start up?

One of the biggest traps new Ubuntu users fall into is getting hung up on specific details of a task, rather than the process as a whole. Yes, it is true one needs Wine to install netflix-desktop. However, if you get hung up on that one step, you will "miss the forest for the trees."

The netflix PPA **contains its own patched version of wine** that is separate from the "regular" wine in the Ubuntu repositories. You can have one or the other or both installed; the patched wine is **only** for using netflix and nothing else.

Please carefully follow the "how to install" instructions in post #1 of this thread step-by-step:

[http://ubuntuforums.org/showthread.php?t=2084592](http://ubuntuforums.org/showthread.php?t=2084592)

If you have any problems/errors, then copy & paste the **complete** terminal output (not just the part you think is relevant) in that thread, and you will get the help you need. Good luck!

(edit) I am not 100% sure this will even work in WUBI as opposed to a regular install... suggest asking in that thread I linked to. ;)

---

### Post by zaospawn on 2013-02-21
I do not intend on fully switching over to Ubuntu. Instead I went the Wubi route. I still use Windows 7 (dual boot) for most of my entertainment needs but it would still be nice to be able to do fun stuff on Ubuntu when taking a short break from code writing. The learning curve for Linux became a glaring reality when I realized I do not know how to install things outside the Software Center. The fact I could not do a simple install on the terminal sent off red flags and that is why I sounded so childish in my initial post. 

Anyways...

Okay I just tried it and I ran into the same brick wall again. The first two commands worked fine but when I typed in the third one "sudo apt-get install netflix-desktop" here's what I get in it's entirety:

> brian@ubuntu:~$ sudo apt-get install netflix-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 netflix-desktop : Depends: wine-browser-installer but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
brian@ubuntu:~$ 


---

### Post by nwalkey on 2013-02-21
Maybe try 'sudo apt-get -f install netflixpackagename'. The -f will try to fix broken dependencies. If that doesn't work try installing the dependency that it says it wasn't going to install before installing netflix. If you have a bit of patience with linux and take some joy in messing around with how your operating system works you will find the learning curve is no problem.

---

### Post by snowpine on 2013-02-21
It is possible this doesn't work on WUBI (I've never used WUBI before, I just don't know) and therefore I would encourage you to ask the experts in the "netflix on ubuntu" megathread I linked to above. Good luck! :)

---

### Post by zaospawn on 2013-02-21
So I take it from that error message I sent you there's nothing in there to help diagnose this? I have been trying to do it through Synaptic and I keep getting error messages about dependencies and broken packages.

---

### Post by snowpine on 2013-02-21
nwalkey has a good suggestion to try:

```
sudo apt-get -f install
```

Did you try it?

Beyond that, I encourage you to ask the netflix experts in the "netflix on ubuntu" thread I linked to above. It is more likely that a netflix expert looking to share his/her knowledge will stumble upon your question in that thread than in one titled "new to linux, can't install anything!" Remember that you are installing 3rd-party software not provided or supported by the makers of Ubuntu, so be patient. :)

---

### Post by zaospawn on 2013-02-21
I am starting to wonder if this is more of a Wubi issue. Anyways I just tried what you recommended Nwalky and here's what I got:

> brian@ubuntu:~$ sudo apt-get -f install netflix-desktop
[sudo] password for brian: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
brian@ubuntu:~$ 

 I don't want to be dependent on the Software Center for all of my downloads and I feel that if I can't master installing basic things through the terminal I will never master Linux. Most of the help I have found is either riddled in computer science jargon or it is geared towards advanced Linux users. I apologize for this rant, I have been so excited about trying something new and I am about ready to give up :/

---

### Post by snowpine on 2013-02-21
I would in fact encourage you to use Software Center for best stability and security. Only on rare exceptions (such as the unsupported 3rd-party app netflix-desktop) should you go outside the Software Center. When you try the command in my post #9, copy & paste so there are no typos, then you shouldn't get the "invalid command" error. :)

---

### Post by zaospawn on 2013-02-21
> **snowpine said:**
> I would in fact encourage you to use Software Center for best stability and security. Only on rare exceptions (such as the unsupported 3rd-party app netflix-desktop) should you go outside the Software Center. When you try the command in my post #9, copy & paste so there are no typos, then you shouldn't get the "invalid command" error. :)

I tried it type-o free and here's what I got:

> brian@ubuntu:~$ sudo apt-get -f install netflix-desktop
[sudo] password for brian: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
brian@ubuntu:~$ 			 		

Anyways I just want to say, thank you for your patience, politeness, and diligence. I understand this third-party stuff is outside your typical arena. My biggest concern is being unable to install anything outside of the Software Center, even something as simple as Java so I can run certain apps off browsers.

---

### Post by snowpine on 2013-02-21
That error means another process (Software Center, Synaptic, Update Manager, apt-get in another terminal, etc.) is already running. Close it, and then try again.

Here are instructions to install Java: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Good luck--I am signing off to go watch a netflix! ;)

---

### Post by JiuJitsu500 on 2013-02-21
When it says "cannot get a lock on /var/lib/...." That means you might be running synaptic package manager, software center, or otherwise apt-get is running somewhere.

Open up activity monitor and kill any processes like software-center, synaptic, apt-get, jockey-gtk, update manager,...

Then retry

Linux only allows one thing to install one thing at a time. Everything has to wait in line - but all use the same apt-get to do it from the repositories.

---

### Post by zaospawn on 2013-02-21
> **JiuJitsu500 said:**
> When it says "cannot get a lock on /var/lib/...." That means you might be running synaptic package manager, software center, or otherwise apt-get is running somewhere.

Open up activity monitor and kill any processes like software-center, synaptic, apt-get, jockey-gtk, update manager,...

Then retry

Linux only allows one thing to install one thing at a time. Everything has to wait in line - but all use the same apt-get to do it from the repositories.

How do you open activity manager? I can't find it anywhere.

---

### Post by zaospawn on 2013-02-21
Couldn't find it but I was able to kill some processes that I know of and here's what I got this time...

> brian@ubuntu:~$ sudo apt-get -f install netflix-desktop
[sudo] password for brian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 netflix-desktop : Depends: wine-browser-installer but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
brian@ubuntu:~$ 

---

### Post by zaospawn on 2013-02-21
I think I am going to give up on third party software and just use what's available from the Software Center. As regular Linux users, do you use many third party software? Also is it important to have?

---

### Post by carl4926 on 2013-02-21
There is an option in Synaptic to Fix Broken Packages, did you try this?

---

### Post by zaospawn on 2013-02-23
> **carl4926 said:**
> There is an option in Synaptic to Fix Broken Packages, did you try this?

I clicked on it and nothing seemed to happen. Oh, well.

---

### Post by carl4926 on 2013-02-23
Can I just point you to this earlier reply
[http://ubuntuforums.org/showpost.php?p=12523103&postcount=4](http://ubuntuforums.org/showpost.php?p=12523103&postcount=4)

Please note the points made there.

I can't comment on Wubi, never used it. It's not a proper installation though. I'd liken it to a bike with stabilizers. You know, like they use for infants.

As for Netflix, I have no idea either. Don't use it and probably never will.

---

### Post by zaospawn on 2013-02-23
> **carl4926 said:**
> Can I just point you to this earlier reply
[http://ubuntuforums.org/showpost.php?p=12523103&postcount=4](http://ubuntuforums.org/showpost.php?p=12523103&postcount=4)

Please note the points made there.

I can't comment on Wubi, never used it. It's not a proper installation though. I'd liken it to a bike with stabilizers. You know, like they use for infants.

As for Netflix, I have no idea either. Don't use it and probably never will.

I figured it out. Elsewhere someone mentioned first trying to install it via

> sudo aptitude install <packagename>

After doing that it fixed everything then when I tried installing netflix again it went ahead and installed all the dependencies and then netflix and now it is up and running. Consider this problem solved. :)

Thank you all for your diligence and patience. I look forward to discussing more productive things about Ubuntu with everyone in the future :)

):P

---


---
title: "Stuck Early In Installation"
date: 2010-09-13
forum: Installation &amp; Upgrades
---

### Post by yodaismycopilot on 2010-09-13
Hello:

This is my first post. I have an old computer with a 1 Ghz processor and 224K ram and decided to install Ubuntu over Windows ME. After the screen with the red & white dots transformed into the screen that looked like some deep space purple nebulae, I got a box that simply said "Login." So I typed something and pressed "enter" then I got a box that said "password." And then I typed something and pressed "enter." Then I got an "authentication failure" message. 

This step is not mentioned in the information I found online:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

I thought I was supposed to get a battery of questions to answer...

Why is there so many problems with this? There is zillions of problems posted online and everyone acts like it's normal. This is very frightening. I took a unix class at the local community college and an introductory C programming course and did very well in both. But that is the extent of my background.

Thank you for your understanding and any possible solutions or advice.

---

### Post by TNT1 on 2010-09-13
You booted a live cd?

When you booted there should have been some options, like try ubuntu without making changes/
boot from first HD/
check disc/

and so on. 

You may have missed those, and it defaulted to live os environment. you can try user and root at login there, or root and root.

---

### Post by yodaismycopilot on 2010-09-13
Nope. Just went from one screen to the next as I described. I was watching closely the whole time. But thanks. I'll go try your login suggestions.

---

### Post by TNT1 on 2010-09-13
> **yodaismycopilot said:**
> 

I thought I was supposed to get a battery of questions to answer...
.

What version are you installing, and what are you installing from?

---

### Post by yodaismycopilot on 2010-09-13
The newest version 10.2. 

The weird thing is that every time I try to install, something different happens. After my last post I went back to try the password suggestions above, but that screen never appeared!!! Instead, it looked like the install was proceeding normally, but very slow, like 20 or 30 minutes just to get to the screen where you answer the questions and then it would pause for minutes before asking me the subsequent question.

Then I was given a message: "ubi-migration assistant failed with exit code 126. Further information may be found in /var/log/syslog. Do you want to try running this step again before continuing? If you do not, your installation may fail entirely or may be broken."

I clicked a few times to "try again," but nothing happened. My button choices were "QUIT," "CONTINUE ANYWAY," and "TRY AGAIN."  So then I pressed "continue anyway."

Then I got the message "ubi summary crashed."

Then I got a box saying "The installer encountered an unrecoverable error. A desktop session will now be run so that you may investigate the problem or try installing again." With an "OK" button. I pressed "OK."

Then I got the message: "General error mounting filesystems. A maintenance shell will now be started. Control-D will terminate this shell and reboot the system.
root@ubuntu:~#_"

It just sat there and did nothing. So I pressed ctrl-D.

Then I tried a few times to reinstall but I just get the screen with the little red dots turning white, then turning red again. Also, my cd rom drive is clicking and chattering really loud.

This is where I'm at. Thanks everyone! I am new to this. Wow! By looking at the posts on this forum, there SURE are a lot of problems people have with Ubuntu! (Why is this?)

Any advice is appreciated!

---

### Post by Rubi1200 on 2010-09-13
The problem surely has to do with the computer specifications?
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Try downloading and burning to CD another version like Lubuntu and give that a go instead.

---

### Post by pastalavista on 2010-09-13
Yes, the live CD needs a lot more ram to run than an installed system. Try downloading the "Alternate Version" that installs with a simple text based installer. That is if you want to run Ubuntu. You might also try a [Minimal Install]("https://help.ubuntu.com/community/Installation/LowMemorySystems") or add more RAM.

---

### Post by yodaismycopilot on 2010-09-16
So I took the suggestion above and torrented the "alternative" installation that is supposed to be less memory intensive. I ended up with a blank blue screen with nothing on it and nothing happening. Here's the blow by blow...

Got a message: "Attempting to find an available wireless network failed.

wlan0 is a wireless network interface/ Please enter the name(the ESSID) of the wireless network you would like wlan0 to use. To skip wireless configuration and continue, leave this field blank."

So I decide to skip since I have no idea what to enter.

I get : "configuring the network with DHCP. This may take some time."

Then: "Network autoconfiguration failed. Your network is probably not using the DHCP protocol. Alternatively, the DHCP server may be slow or some network hardware is not working properly."

Then I selected "Do not configure the network at this time." 

Here I was hoping I could get a Linux desktop and fuss with the internet later. I was prompted for a time zone and a few things, then my screen went unresponsive and blue and completely blank.

This is really obnoxious. I think I have an old Linspire CD somewhere. Should I give that a try?

Thanks everyone for your help.

---


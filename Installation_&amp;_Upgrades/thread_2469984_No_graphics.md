---
title: "No graphics"
date: 2021-12-16
forum: Installation &amp; Upgrades
---

### Post by DavidS on 2021-12-16
I have been running Ubuntu 20.04 for about a year.  A few months ago, after an upgrade to kernel 5.11.0-41, the GUI wouldn't start.  I tracked this down to a bug in the nvidia driver, which was widely reported and still seems to be a problem.  However, I was able to run my previous 5.8.0-63 kernel OK until today.  Now I get no graphics with that kernel either.

I still have a working Ubuntu 18.04 on another partition, so I booted that up, and it works OK complete with graphics.  Looking at Software and Updates I found that under 18.04 I was using the nouveau driver and not nvidia at all.  So that seemed to be the answer: get rid of nvidia altogether, and then (so I was led to believe) the nouveau driver would be automatically loaded.

I went back to a root terminal in 20.04 and removed all the nvidia stuff.  But when I reboot any of the Ubuntu 20.04 versions, I still get no GUI.

How can I get this working without having to do a complete re-install?

David

---

### Post by MAFoElffen on 2021-12-16
So when you boot into your 20.04 Instance, at the Grub Menu, press <E> to edit, go down to the line starting with "linux", and replace the text "quit splash" with "nosplash --verbose nomodeset"... then Press <Cntrl><X> to boot.

While it is booting, note the onscreen messages and check for errors. Tell me if the GUI starts... Note how long it took to boot up to that point... Time it. If the GUI comesup, go to the link in my signature line for the UbuntuForums 'system-info' script. Start a terminal session and download the script to somewhere that you remember where it is in your Home directory, but do not run it yet...
```

wget -N -t 5 -T 10 https://github.com/Mafoelffen1/system-info/raw/main/system-info && \
chmod +x system-info

```
That will download it and make the script executable, to any directory, that your had issued that command...

Not reboot. Let it boot normally this time. When it has booted... (same time that you noted), Press <Cntrl><Alt><F4>. It should swith oer to a Virtual TTY session (TTY4)... Log in. Navigate to the disrectiory your saved the script, and run it:
```

./system-info

```
Choose to upload it to a Pastebin, so you can post a link to it here, in a post.

Running the report like that, under those circumstances, will tell us what hardware you have, and the current settings, where the problem is occurring, and tell us enough information for us to make an informed recommendation.

Please keep me posted if you have problems, what is going on, or if you need anything explained.

---

### Post by MAFoElffen on 2021-12-17
> **albert902 said:**
> There are a few reasons why Ubuntu may not be displaying graphics correctly. One possibility is that your graphics card is not supported by Ubuntu. Another possibility is that the drivers for your graphics card are not installed or are not working properly. You can troubleshoot this by visiting the Ubuntu website and searching for information on how to install the correct drivers for your graphics card. If you still experience problems after installing the correct drivers, you may need to update your BIOS or switch to a different graphics card.
Back up, listen and learn please. You seem to be a little confused. The buck stops "here". The Ubuntu Community Support described everywhere around the world, in the Distro installation scripts, and on Ubuntu.com, are all linked back here to UbuntuForums.org (here).

> **albert902 said:**
> One possibility is that your graphics  card is not supported by Ubuntu.
There are [COLOR=#ff0000]very few[/COLOR] Graphics Cards that I have not been able to get to work with Ubuntu (or rather Linux), in some form or another... And they were not NVidia. And those f*ew *were not supported by the Linux Graphics layer itself.

Have you read my "Graphics Resolution" Sticky in this Section of the forums? Modestly, that is where a lot of the Wiki Graphics Pages and Graphics Tutorials are based from. I have just been helping people for a long time.

 We do not turn people away, back into the cold, and tell then to solve their issues on their own... We identify the problem and help them to resolve it (here). We share our experience in solving problems and make Ubuntu work for them on their hardware. That is our Community Support system and how we help others. That is what my Ama-Gi Ubuntu Support LiveCD Project is about. A tool-set for helping Users to repair their installed systems.

I am trying to be kind, be a mentor, and to help you also. I am trying not to pick apart what you said... in so many ways... NVidia GPU's have a special place in my life. I have been supporting them for Linux, UNIX and Windows for over 16 years, as well as many other graphics cards. (and the Linux Graphics Layer as a whole.) We do not tell people to "just switch graphics cards" blindly.... without finding out what they have, and research what the current support for it is. Even then, some things can be done. There may be limitations, but well...

Please. You should not make blanket statements without first finding out what the user has, what is installed and configured, and what the problem is. That is why the system-info script exists, and why is was approved and endorsed by the Forum. Find out information on the system and settings, so a helper can make an informed recommendation on solutions. Without that information, you are making a blind guess, and hoping that you stumble onto what "may be" wrong.  That was my intent when I wrote the UbuntuForum's 'system-info' script for the Ubuntu Member's and other User's here... To help User's that are having problems. Many people here, helped with making it what it is today, with ideas on what it should contain, and in testing it to make sure it worked for all editions, and flavors of Ubuntu, as well as it being safe, and secure.

Make your life easier and learn to use it as a tool in your diagnostics. Learn how to interpret the results of it's report, and what they mean.

EDIT: There was a specific Ubuntu Linux Kernel Update, just like the OP described, that did not work on some certain hardware combinations, with NVidia drivers, in any form of those drivers... That is known and true. Like the OP described, when it happened, the fix was to use a previous kernel. We need to see what is installed, what the hardware is, and how it is configured.

---


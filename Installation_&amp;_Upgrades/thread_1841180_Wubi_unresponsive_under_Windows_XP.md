---
title: "Wubi unresponsive under Windows XP"
date: 2011-09-08
forum: Installation &amp; Upgrades
---

### Post by J-mz on 2011-09-08
Does anyone have experience with Wubi simply not running?
I've downloaded several versions, and also tried running it from a live CD of 10.10.
In each case, the disc spins for a few seconds, and the process gives up.

I've used that same live CD to successfully install 10.10 (using Wubi) on another machine under Windows Vista, no problems.

I recently installed Windows XP Service Pack 3 - somewhat reluctantly - in hopes that Wubi would run under that, but it didn't help.

Thanks,

James.

---

### Post by bcbc on 2011-09-08
Is it possible that you have python installed? That's a known [issue]("https://bugs.launchpad.net/bugs/819318").

Otherwise, you can look for the log file and see if there are any clues. If you're running 11.04 you can find it in:
%temp%\wubi-11.04-rev211.log

---

### Post by J-mz on 2011-09-08
Thank-you.  That sounds hopeful.
I'm sorry to say that I don't know how either to check whether I have python installed, or to remove the python path...

---

### Post by J-mz on 2011-09-08
Interesting - I note that in this thread 
[https://bugs.launchpad.net/wubi/+bug/365501](https://bugs.launchpad.net/wubi/+bug/365501)
people are having this issue on Thinkpads.  
I'm also using a Thinkpad - R51.

---

### Post by bcbc on 2011-09-08
> **J-mz said:**
> Thank-you.  That sounds hopeful.
I'm sorry to say that I don't know how either to check whether I have python installed, or to remove the python path...

See here: [http://support.microsoft.com/kb/310519](http://support.microsoft.com/kb/310519)

You probably want to write down the old settings so you can restore them later.

I think if you go to a commmand prompt you can override the environment variables just for that command prompt session. You can manipulate them as follows:

This lists all environment variables: set
This lists a specific variable: echo %path% 
This changes a specific variable: set path=xxxx
This clears an environment variable: set path=
You can also run wubi.exe from a command prompt. So you should be able to test it that way.

---

### Post by J-mz on 2011-09-09
Thanks! 

Python seems to have been the problem.

I followed the workaround posted by petebisson at the link below.

See Thinkpad Workaround to use Wubi 9.04 at   
[https://bugs.launchpad.net/wubi/+bug/365501](https://bugs.launchpad.net/wubi/+bug/365501) 

Cheers,

James.

---

### Post by bcbc on 2011-09-09
Ok great. I'm remember that workaround as well for future use. That's an old bug that should be fixed by now.

I'll put that workaround here as well in case other people find this thread. (And you can mark the thread as Solved from the Thread Tools menu.)
> Thinkpad Workaround to use Wubi 9.04

1. Right click on My Computer, select Properties
OR
Go to Control Panel -> System

2. On the 'Advanced' tab click the 'Environment Variables' button.

3. In the bottom pane ('System Variables') scroll down the list until you find the PYTHONCASEOK variable.

4. Highlight the PYTHONCASEOK line and click the 'Delete' button. (Just changing the value will not work.)

5. Reboot your thinkpad.

6. Run wubi.exe, and enjoy :-)

7. After installing wubi, you need to re-add PYTHONCASEOK with a value of 1 or your assorted IBM tools will not work.

NOTE: You will also need to repeat steps 1-5 if you want to uninstall wubi in the future, as the wubi uninstaller will have the same problem. Don't forget to do step 7 again after running the wubi uninstaller.

---


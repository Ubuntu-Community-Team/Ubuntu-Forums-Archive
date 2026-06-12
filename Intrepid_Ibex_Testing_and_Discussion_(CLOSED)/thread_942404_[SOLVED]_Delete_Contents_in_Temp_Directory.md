---
title: "[SOLVED] Delete Contents in Temp Directory"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Sef on 2008-10-09
My temp directory has some items that seem to be there permanently.   I have tried 'sudo apt-get autoremove' and 'sudo apt-get clean', but the files are still there.  I am unable to download because the temp directory is so full.

This is what is in it:

> keyring-bTnivD  pulse-sef            seahorse-GYeIU2   virtual-sef.xDJ5s7
orbit-sef       pyvoice_aliases_sef  Tracker-sef.8548


How can I delete the contents?

---

### Post by knarf on 2008-10-09
The first thing to do: find out how much space these directories take up in /tmp:

```

sudo du /tmp|sort -rn|less

```

It is necessary to use sudo because you want to be able to read all directories, including those owned by and limited to others than your user.

What result do you get when you execute the above commands?

---

### Post by Sef on 2008-10-09
Here is the results:

> 32      /tmp
16      /tmp/Tracker-sef.8548
4       /tmp/pulse-sef
4       /tmp/orbit-sef
0       /tmp/.X11-unix
0       /tmp/virtual-sef.xDJ5s7
0       /tmp/Tracker-sef.8548/Attachments
0       /tmp/seahorse-GYeIU2
0       /tmp/plugtmp
0       /tmp/keyring-bTnivD
0       /tmp/.ICE-unix
0       /tmp/.exchange-sef
0       /tmp/.esd-1000


---

### Post by xebian on 2008-10-09
> **Sef said:**
> My temp directory has some items that seem to be there permanently.   I have tried 'sudo apt-get autoremove' and 'sudo apt-get clean', but the files are still there.  I am unable to download because the temp directory is so full.

This is what is in it:



How can I delete the contents?

If your /tmp is '..so full' then create a bigger partition if it's on a separate partition.  If not then your / partition is not big enough.

IMO this /tmp is for temporary stuff so you can get rid of them safely after a session.  Normally they have cron jobs that go purging these files just before logout.  That's why when you shut down, it doesn't go blank 'pronto' because it executes all these cleanup jobs.  I noticed that Tracker seems to be filling it up.  

apt-get autoremove and clean are only for the apt stuffs which are in the /var/cache/apt/archives

---

### Post by Sef on 2008-10-09
> IMO this /tmp is for temporary stuff so you can get rid of them safely after a session. Normally they have cron jobs that go purging these files just before logout. That's why when you shut down, it doesn't go blank 'pronto' because it executes all these cleanup jobs. I noticed that Tracker seems to be filling it up.

But it is not cleaning it out.   As noted above, 'clean' does not work.

---

### Post by FuturePilot on 2008-10-09
apt-get autoremove only uninstalls packages that have no programs that need them as dependencies. apt-get clean cleans out /var/cache/apt/archives. Neither are related to anything in /tmp. When you say downloading do you mean problems downloading updates with apt-get or downloading in general such as through a web browser?

---

### Post by wgrant on 2008-10-09
> **Sef said:**
> But it is not cleaning it out.   As noted above, 'clean' does not work.

Stupid Firefox, not letting me run Windows.

---

### Post by doas777 on 2008-10-09
I assume youve tried ```
 sudo rm -rf /tmp/*
``` ?


[COLOR="Red"]DISCLAIMER: THIS IS A POTENTIALLY DANGEROUS COMMAND> ENSURE THAT YOU ARE REMOVING ONLY WHAT YOU WANT TO REMOVE WITH "rm -rf"[/COLOR]

---

### Post by wgrant on 2008-10-09
More seriously...

apt-get clean and apt-get autoremove deal with apt. apt != /tmp.

Also, applications don't just put stuff in /tmp for the hell of it - they need it there. If it's there after a reboot, it has very probably been recreated for good reason (/tmp is generally a tmpfs). Nothing in your directory listing of /tmp is abnormal. Are you sure that /tmp is actually full?

---

### Post by Sef on 2008-10-09
> I assume youve tried  	Code:
 	 sudo rm -rf /tmp/* 
 ?

Thank you.  I was not sure of the exact code, and did not want to do willy-nilly.

---

### Post by Sef on 2008-10-09
> Nothing in your directory listing of /tmp is abnormal. Are you sure that /tmp is actually full?

I was unable to download another os and opera because it kept saying that my temp file was full.   I have small hard drive - about 40 GB.

---

### Post by mc4100 on 2008-10-09
> **Sef said:**
> I was unable to download another os and opera because it kept saying that my temp file was full.   I have small hard drive - about 40 GB.

Have you tried using bittorrent instead of a web browser?

---


---
title: "Seemingly Random Lockups in Jaunty"
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by bcrook88 on 2009-04-04
I did I clean install of Jaunty beta and have been experiencing lockups of my laptop at unpredictable times. When it locks any sound playing is stuck repeating, mouse and keyboard do not respond and my activity applets on my panel lock. I can alt+SysRq+REISUB out of it or hold down the power button.

I have looked through the logs but I can't seem to find any error messages or anything. 

The lockups seem to happen when I am using Hellanzb or Sabnzbd, but sometimes they don't cause any issue. 

Any help in tracking down this problem would be greatly appreciated!

Thanks!
Dell Inspiron 630m
Jaunty Beta 2.6.28-11-generic

---

### Post by olskar on 2009-04-04
> **bcrook88 said:**
> I did I clean install of Jaunty beta and have been experiencing lockups of my laptop at unpredictable times. When it locks any sound playing is stuck repeating, mouse and keyboard do not respond and my activity applets on my panel lock. I can alt+SysRq+REISUB out of it or hold down the power button.

I have looked through the logs but I can't seem to find any error messages or anything. 

The lockups seem to happen when I am using Hellanzb or Sabnzbd, but sometimes they don't cause any issue. 

Any help in tracking down this problem would be greatly appreciated!

Thanks!
Dell Inspiron 630m
Jaunty Beta 2.6.28-11-generic

Using a nvidiacard?

---

### Post by bcrook88 on 2009-04-04
Thanks olskar for the reply,

Its not an Nvidia card, its an Intel 915GM integrated card.

It just happened again and seems to be related to the Sabnzbd newsgroup downloader.

---

### Post by Yashiro on 2009-04-04
Which type of filesystem is Sabnzbd writing to?

---

### Post by macroshaft on 2009-04-04
I have also been experiencing this but not related to any specific program as far as I can tell. Mine is also an intel graphics card. (Acer aspire 5315)

---

### Post by bcrook88 on 2009-04-04
It's EXT4...I am hoping that this isn't the issue. I really like it.

It seems to explode during the processing part (par check, extraction, and then moving/renaming the folder). But, I can't be sure.

---

### Post by Yashiro on 2009-04-04
I'd guessed it was ext4, yeah. It's possible it's some kind of soft locking bug thats been mentioned in here a few times.

---

### Post by bcrook88 on 2009-04-04
Thanks Yashiro,

Do you know of any way to prove it? Log files to check?

---

### Post by Yashiro on 2009-04-04
dmesg, syslog, kern.log perhaps. The usual culprits.

---

### Post by bcrook88 on 2009-04-04
Thanks. I looked around in there every time it locked up...nothing. 

I will get around to formatting to EXT3 and report back.

Thank you for your help!

---

### Post by RAOF on 2009-04-04
You may well be seeing bug [lpbug]330824[/lpbug].

---

### Post by Yashiro on 2009-04-04
Well it is only a mildy educated guess. You might want to look into other causes before a reformat.

---

### Post by bcrook88 on 2009-04-04
> **RAOF said:**
> You may well be seeing bug [lpbug]330824[/lpbug].

I will try to cause it this way. Sabnzbd could be causing it when deleting the .rar files left over.

It appears to be this bug. I attempted to empty my trash and it locked up before anything got deleted. Thank you everybody for your help...I will follow the linked bug report

---

### Post by mykrob on 2009-04-07
I have had a few lockups today all of a sudden..

I am using EXT3 file system, and this is installed on my Gateway laptop with Intel 945GM graphics.

Didnt occur at all in Intrepid.

Looking for troubleshooting assitance..

What info do you need from me to be able to help?

Thanks,
-myk

---

### Post by mykrob on 2009-04-08
Happened again...

What information can I provide to begin to log a possible bug report?
I know this may be resolved in an upcoming update, though..

Seems like an update introduced the behavior...

difficult to trace since it cannot be isolated to a specific event

---


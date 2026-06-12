---
title: "Can't upgrade to 10.10 &quot;Unable to correct problems, you have held broken packages.&quot;"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by avada on 2010-10-09
I get this error:
```
An unresolvable problem occurred while calculating the upgrade:
E:Unable to correct problems, you have held broken packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu
```
So I have "Unofficial software packages" I guess. I have a few ppa-s added. And using some packages (eg: xserver-xorg-video-radeon, wine). What should I do now?

I also get a warning on the console: "WARNING: Failed to read mirror file"

---

### Post by clrg on 2010-10-09
I think I found the problem:

>  This can be caused by:
 * Upgrading to a pre-release version of Ubuntu

10.10 is due tomorrow, not today.

---

### Post by avada on 2010-10-09
> **clrg said:**
> I think I found the problem:



10.10 is due tomorrow, not today.
Well yeah. That's why i used the -d switch. I thought there wouldn't be any significant changes (if any), between today and tomorrow.

---

### Post by insaini on 2010-10-10
> **avada said:**
> Well yeah. That's why i used the -d switch. I thought there wouldn't be any significant changes (if any), between today and tomorrow.

i have the same issue...  with some ppa's setup..

how do we resolve this ?

---

### Post by insaini on 2010-10-10
ok that was relatively painless..

just purged the xorg-edgers ppa and upgrade is now going through..

cheers

---

### Post by avada on 2010-10-10
> **insaini said:**
> ok that was relatively painless..

just purged the xorg-edgers ppa and upgrade is now going through..

cheers
By purging you mean removing all packages from that ppa? Anyway I just made a clean install.

---

### Post by fr4nko on 2010-10-10
Hi,

I have the same problem. How did you purge the xorg-edgers package ?

Francesco

---

### Post by webmadman on 2010-10-11
To purge use ppa-purge. Install it with:

```
sudo apt-get install ppa-purge
```

And to purge the xorg-edgers packages:

```
sudo ppa-purge xorg-edgers
```

You can use it for any ppa's- handy as all-get-out!

I thought this might be an issue, haven't done the upgrade yet, but came here and did a search first- glad I did- thanks for the questions and answers :)

---

### Post by Noccy on 2010-10-16
> **insaini said:**
> ok that was relatively painless.. just purged the xorg-edgers ppa and upgrade is now going through..

How are the after effects? The reason I installed the xorg-edgers ppa on my 10.04 Acer Aspire One is because the video performance was horrible without it.

On a sidenote, I'm also curious if anyone with the same setup use a USB wireless broadband modem that requires usb-modeswitch, and if so how that setup works with 10.10.

---

### Post by Rim3nX on 2011-02-11
It seas to me "Warning:  Could not find package list for PPA: xorg-edgers ppa" and I still get the "Could not calculate the upgrade" message.
What should I do ?

---

### Post by avada on 2011-02-11
> **Rim3nX said:**
> It seas to me "Warning:  Could not find package list for PPA: xorg-edgers ppa" and I still get the "Could not calculate the upgrade" message.
What should I do ?
Delete all PPAs and conflicting packages.

---

### Post by bbd92b on 2011-02-28
> **Rim3nX said:**
> It seas to me "Warning:  Could not find package list for PPA: xorg-edgers ppa" and I still get the "Could not calculate the upgrade" message.
What should I do ?
Same problem here, mate, already deleted all ppa's my brain can't figure out anything else that can be done

---

### Post by madhusker on 2011-05-28
> **webmadman said:**
> To purge use ppa-purge. Install it with:

```
sudo apt-get install ppa-purge
```

And to purge the xorg-edgers packages:

```
sudo ppa-purge xorg-edgers
```

You can use it for any ppa's- handy as all-get-out!

I thought this might be an issue, haven't done the upgrade yet, but came here and did a search first- glad I did- thanks for the questions and answers :)

Solved.  See [http://ubuntuforums.org/showthread.php?t=1325260](http://ubuntuforums.org/showthread.php?t=1325260)

---


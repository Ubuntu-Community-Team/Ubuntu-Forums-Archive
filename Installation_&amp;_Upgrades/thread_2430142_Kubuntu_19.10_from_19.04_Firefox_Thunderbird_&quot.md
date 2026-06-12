---
title: "Kubuntu 19.10 from 19.04 Firefox Thunderbird &quot;using an older version&quot;"
date: 2019-10-28
forum: Installation &amp; Upgrades
---

### Post by divirtual on 2019-10-28
After upgrading from Kubuntu 19.04 to 19.10, both Firefox and Thunderbird stopped working for me.  If I attempted ...

```
firefox -p

thunderbird -p
```

... in both cases, I would get the message about "... using an older version ... create a new profile ....".  

With Kubuntu 19.10, we're at Firefox 70, and Thunderbird 68.  There was a previously reported issue "[Firefox 67 thinks it's an old version and won't load my profile]("https://bugzilla.mozilla.org/show_bug.cgi?id=1553554")" with a status of "resolved wontfix".

The interesting wrinkle is my computer is a multi-boot Thinkpad, and I'm spending most of my time in (rolling release) Manjaro.  So, under Manjaro, Firefox 70 opens just fine!  


I found an lead in "[Updating to Firefox 67 switches to a new Profile, makes users worry about old profile]("https://techdows.com/2019/05/switch-to-old-profile-from-new-profile-in-firefox-67.html")", May 2019, in a response by "Your Pal":

```
This worked for me, thank you.
On MacOS in Terminal:
&#8211; cd to /Applications
&#8211; run &#8220;open Firefox.app &#8211;args &#8211;allow-downgrade&#8221; (without quotes)


```

So, under Linux, I tried:

```
firefox -args -allow-downgrade

thunderbird -p -args -allow-downgrade

```

... which allows both Firefox and Thunderbird to start normally (and I don't have to repeat it every time).

I think that this is a workaround to correcting a setting somewhere ... and not a remedy going forward.  Now that it's fixed, I can't replicate the original issue.  Maybe if someone else gets this error, they can report back on more diagnostics.

---

### Post by divirtual on 2019-10-29
After booting in Manjaro, and then back into Kubuntu, the problem has returned.  I've now saved a text file on my desktop with:

```
[FONT=&amp]firefox -args -allow-downgrade[/FONT]
[FONT=&amp]
[/FONT]
[FONT=&amp]thunderbird -p -args -allow-downgrade[/FONT]

```
... and may have to reapply that when it recurs.

---

### Post by Impavidus on 2019-10-29
Seems very similar to this one, that happened at an upgrade from 18.10 to 19.04: [https://ubuntuforums.org/showthread.php?t=2420127](https://ubuntuforums.org/showthread.php?t=2420127)
I explained what I did to solve it in post #6. You may want to read the linked bug reports from that thread.

---

### Post by SeijiSensei on 2019-10-30
I upgraded to Kubuntu 19.10 and had none of these issues.  Firefox is at 70.0, and Thunderbird at 68.1.2.  I don't change distributions like you apparently do.  From the description, it does seem to have something to do with switching to Manjaro and switching back again.  Do you have a separate partition for /home that both distros share?

---

### Post by divirtual on 2019-10-30
@SeijiSensei 
> [COLOR=#000000]Do you have a separate partition for /home that both distros share?

Yes, I have one /home partition, and access that via Manjaro 18, Kubuntu 19.10, Ubuntu 16.04 and Deepin Linux.  While the distros change (I recently removed Fedora), the multiboot partitions have been in place since 2013.  

This morning, after a switch to Manjaro and back to Kubuntu 19.10, Firefox and Thunderbird aren't giving me the "using an older version" message, and start normally.  So this thread is mainly to remind myself and others what to do, should the situation arise.[/COLOR]

---


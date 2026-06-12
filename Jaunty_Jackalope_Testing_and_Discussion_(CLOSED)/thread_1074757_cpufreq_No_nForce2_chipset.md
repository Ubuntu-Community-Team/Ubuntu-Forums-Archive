---
title: "cpufreq: No nForce2 chipset"
date: 2009-02-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Elfy on 2009-02-19
mmm - ok I have had along with it seems  a lot of other people a few oddities over the last few days - but I can't see any refernces to this.

After all updates so far today I get this error shortly after boot starts

cpufreq: No nForce2 chipset

While I can boot ok I now have scratchy pulseaudio (I had this anyway, but have a few changes to a couple of files which dealt with that up until this update) and a vaguely unresponsive system - everything works - eventually.

I've spent a while searching the forums and google - but I don't really have a great idea of what it is or does - other than side-effects.

The previous kernel still works ok.

Not even sure what I'm asking help for tbh - but a point in the right direction would be appreciated :)

Edit - if I need to open a bug report then I quite obviously would do so - but wouldn't really know which package I would need to put it against.

---

### Post by ronacc on 2009-02-19
you can file a bug against "unknown" and whoever triages it will assign it to a package , hang in there for awhile though, lots of changes comming through right now , many things are temporarily crossed up .

---

### Post by Elfy on 2009-02-19
thanks ronacc - I was intending to leave it a day or so before I did post a bug - waiting to see what turned up in the morning :)

I seem to get a bunch first thing :)

Thanks for the reply - if it does get resolved I will be sure to post here - if not I will link to the bug report

---

### Post by ronacc on 2009-02-19
if you updated in the early morning you might want to update again 6AM east coast US update broke my box another aroumd 10 AM fixed it (mostly) I usualy update AM and PM .

---

### Post by BwackNinja on 2009-02-19
hmm... I get this too

---

### Post by autocrosser on 2009-02-20
I'm sure that it's a "sniffer" for nvidia chipsets--my last motherboard (EVGA 750i FTW) used a nforce2 chipset for drive control...so that makes sense at that time in the boot --there were lots of changes with the newest kernel, so I would guess that something else is causing your problems---You might look at the diff file to see if anything stands out......

---

### Post by Elfy on 2009-02-20
@bwackninja - well I guees I'm sort of glad it's not just me - but ;)

@autocrosser - hi and thanks for that - I would love to look at the diff file but I have no idea what or where it is - perhaps that will be todays thing to learn :)

---

### Post by The Cokeaholics on 2009-02-20
> cpufreq: No nForce2 chipset
Bug (or is it only a notification?) confirmed (on NVIDIA 9600GT)

Robert

---

### Post by DougieFresh4U on 2009-02-20
I am getting the same "messege" as well. Also there is another line underneath that messege, but I haven't been able to get the whole thing as it goes by real fast, but it's saying something about 'fail' is the last word in it

---

### Post by Elfy on 2009-02-20
I only appear to have the single error - from dmesg

[    1.449034] Freeing initrd memory: 7446k freed
[    1.449470] cpufreq: No nForce2 chipset.
[    1.450258] audit: initializing netlink socket (disabled)

Can't find the 'bug' report though.

Edit - I booted it and had a look at xorg.0.log - nothing seems to be amiss in there.

---

### Post by Elfy on 2009-02-20
OK - I appear to have found something - processor is being run at 317MHz instead of 2.53GHz - which would seem to account for the 'vaguely unresponsive system' :p

Bug report is here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332170](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332170)

---

### Post by tawmas on 2009-02-20
> **forestpixie said:**
> OK - I appear to have found something - processor is being run at 317MHz instead of 2.53GHz - which would seem to account for the 'vaguely unresponsive system' :p

Bug report is here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332170](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332170)

Yes, I had it running at 350 MHz here. I think that's because the latest kernel update set the default governor to ondemand. Resetting the governor to performance seems to bring responsiveness back.

EDIT: BTW, I just learned how to do that for the current session. Do you know how to do that across reboots?

---

### Post by Elfy on 2009-02-20
I tried 

cpufreq-selector -g performance

and got 

Error calling SetGovernor: Message did not receive a reply (timeout by message bus)

So I'm still unfortuantely still using the older kernel :(

---

### Post by tawmas on 2009-02-20
> **forestpixie said:**
> I tried 

cpufreq-selector -g performance

and got 

Error calling SetGovernor: Message did not receive a reply (timeout by message bus)

So I'm still unfortuantely still using the older kernel :(

I think you need to use sudo to do that. I did.

---

### Post by go7Ul1ai on 2009-02-20
This is also happening to me to, I hope it gets fixed soon :(

---

### Post by Elfy on 2009-02-20
> **tawmas said:**
> I think you need to use sudo to do that. I did.

mmm - that was a particularly :d'oh: moment 

Yep so now as you the it needs to be done on reboot

I shall add that to the bug

If you are both suffering the same thing then it might be of use to confirm it.

---

### Post by tawmas on 2009-02-20
> **forestpixie said:**
> mmm - that was a particularly :d'oh: moment 

Yep so now as you the it needs to be done on reboot

I shall add that to the bug

If you are both suffering the same thing then it might be of use to confirm it.

Confirmed on LP. I'm googling for a way to set the default governor, but found nothing applicable so far. :-( I hope somebody here can help.

---

### Post by Elfy on 2009-02-20
I'm sure someone will somewhere, somewhen - in the meantime at least I can use the newer kernel

---

### Post by Scotty Bones on 2009-02-20
I also have the same nForce2 chipset error and poor performance.
This wasn't an issue with a fresh install of alpha 4.  I don't recall seeing this error message occur till after the update that fixed the crashing greeter problem. **If** my memory is right that might help narrow the window in pinning down the update that caused the issue.

---

### Post by Elfy on 2009-02-21
You're memory is right - but as I updated that time after all the gdm issues I think I missed that actual problem and progressed straight to this one

Edit - apparently there are 2 bugs - one which I reported and is "This is due to the message being printed with KERN_ERR instead of KERN_INFO, but is harmless." - which to me seems a bit odd as if it hadn't printed it would have taken longer to find I expect - at least for me and

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332017](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332017)

which has  a fix committed and I think should deal with the actual issue.

---

### Post by Elfy on 2009-02-22
> **tawmas said:**
> Yes, I had it running at 350 MHz here. I think that's because the latest kernel update set the default governor to ondemand. Resetting the governor to performance seems to bring responsiveness back.

EDIT: BTW, I just learned how to do that for the current session. Do you know how to do that across reboots?

As the fix hasn't appeared yet I have added it to /etc/rc.local

# By default this script does nothing.
cpufreq-selector -g performance

exit 0

---

### Post by tawmas on 2009-02-22
> **forestpixie said:**
> As the fix hasn't appeared yet I have added it to /etc/rc.local

# By default this script does nothing.
cpufreq-selector -g performance

exit 0

I was going to post the same! :-) My only regret is this comes after boot... :-(

BTW, for dual-core CPUs you need to do:

```
cpufreq-selector -c 0 -g performance
cpufreq-selector -c 0 -g performance
```

---

### Post by Stereotypical Rage on 2009-02-22
> **tawmas said:**
> I was going to post the same! :-) My only regret is this comes after boot... :-(

BTW, for dual-core CPUs you need to do:

```
cpufreq-selector -c 0 -g performance
cpufreq-selector -c 0 -g performance
```

Actually for dual-core CPUs it would be: 
```

cpufreq-selector -c 0 -g performance
cpufreq-selector -c 1 -g performance
```

**-c** flag specifies the CPU number.;)

For Quads:

```

cpufreq-selector -c 0 -g performance
cpufreq-selector -c 1 -g performance 
cpufreq-selector -c 2 -g performance 
cpufreq-selector -c 3 -g performance
```

You could do this from the Terminal...but it would not re-appear on reboot unless specified in the manner above.

Dual-Cores
```
sudo cpufreq-selector -c 0 -g performance && cpufreq-selector -c 1 -g performance
```

Quads: 
```
sudo cpufreq-selector -c 0 -g performance && cpufreq-selector -c 1 -g performance && cpufreq-selector -c 2 -g performance && cpufreq-selector -c 3 -g performance
```

---

### Post by tawmas on 2009-02-22
Yep! Silly copy/paste error... Thanks for catching it.

---

### Post by Scotty Bones on 2009-02-22
> **Stereotypical Rage said:**
> Actually for dual-core CPUs it would be: 
```

cpufreq-selector -c 0 -g performance
cpufreq-selector -c 1 -g performance
```


Would this also apply to hyper-thread?

---

### Post by Elfy on 2009-02-24
As of today's updates a couple of things have happened here

firstly the message still appears - ( [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332170](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332170) ) - but this appears to be a seperate issue from

secondly - cpu frequency is now normal without the need for the line in /etc/rc.local ( [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332017](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332017) )

---

### Post by todak on 2009-02-24
Todays update confirms cpu frequency scaling is corrected.
```
dave@kubuntu:~$ cpufreq-info
cpufrequtils 004: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to cpufreq@lists.linux.org.uk, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU

``` Everything running as it should! :KS

---

### Post by Elfy on 2009-02-24
Indeed - now it just feels slow and isn't :(

/me needs new hardware I think ...

---

### Post by tawmas on 2009-02-24
Fixed here too. I've just closed down the launchpad bug.

---

### Post by Elfy on 2009-02-24
+1

after I looked to see which one :)

I still get the annoying message but I can live with that I think :p

---

### Post by hellsgator on 2009-02-24
seems to be working at the correct freq. still getting the message at startup.

analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 800 MHz - 1.87 GHz
  available frequency steps: 1.87 GHz, 1.60 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, userspace, powersave, ondemand, performance
  current policy: frequency should be within 800 MHz and 1.87 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 1.87 GHz:0.00%, 1.60 GHz:0.00%, 1.33 GHz:0.00%, 1.07 GHz:0.00%, 800 MHz:0.00%  (176)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 800 MHz - 1.87 GHz
  available frequency steps: 1.87 GHz, 1.60 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, userspace, powersave, ondemand, performance
  current policy: frequency should be within 800 MHz and 1.87 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 1.87 GHz:0.00%, 1.60 GHz:0.00%, 1.33 GHz:0.00%, 1.07 GHz:0.00%, 800 MHz:0.00%  (274)

---

### Post by Elfy on 2009-02-27
The patched kernel on the bug report deals with the message.

---

### Post by eifel on 2009-03-07
Hi,
can anybody tell me,how i can get cpu-frequency scaling on a Dell Vostro 1700?
With the daily live build in live mode i have got scaling,but as i proceed to install and boot,scaling is gone

Bitte melden Sie Fehler an [email]cpufreq@lists.linux.org.uk[/email].
analysiere CPU 0:
  Treiber: acpi-cpufreq
  Folgende CPUs können nur gleichzeitig ihre Frequenz variieren: 0
  Hardwarebedingte Grenzen der Taktfrequenz: 800 MHz - 2.00 GHz
  mögliche Taktfrequenzen: 2.00 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  mögliche Regler: conservative, userspace, powersave, ondemand, performance
  momentane Taktik: die Frequenz soll innerhalb 800 MHz und 2.00 GHz.
                    liegen. Der Regler "ondemand" kann frei entscheiden,
                    welche Taktfrequenz innerhalb dieser Grenze verwendet wird.
  momentane Taktfrequenz ist 800 MHz.
  Statistik:2.00 GHz:0,00%, 2.00 GHz:0,00%, 1.60 GHz:0,00%, 1.20 GHz:0,00%, 800 MHz:0,00%  (130)
analysiere CPU 1:
  Treiber: acpi-cpufreq
  Folgende CPUs können nur gleichzeitig ihre Frequenz variieren: 1
  Hardwarebedingte Grenzen der Taktfrequenz: 800 MHz - 2.00 GHz
  mögliche Taktfrequenzen: 2.00 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  mögliche Regler: conservative, userspace, powersave, ondemand, performance
  momentane Taktik: die Frequenz soll innerhalb 800 MHz und 2.00 GHz.
                    liegen. Der Regler "ondemand" kann frei entscheiden,
                    welche Taktfrequenz innerhalb dieser Grenze verwendet wird.
  momentane Taktfrequenz ist 800 MHz.
  Statistik:2.00 GHz:0,00%, 2.00 GHz:0,00%, 1.60 GHz:0,00%, 1.20 GHz:0,00%, 800 MHz:0,00%  (141)


As u see the line "driver: acpi-cpufreq" exists.
Is there a way to control the sacling without cpufreq-applet?


PS: Im german and print is from a german jaunty

---

### Post by ubu-for on 2009-03-07
> **BwackNinja said:**
> hmm... I get this too

Me too.

---

### Post by Elfy on 2009-03-07
I still get it too as I didn't bother to reinstall the patched kernel and it is only a message.

I guess it will be dealt with at some point, although ANdy Whitcroft has not returned to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332170](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332170) since he requested confirmation that it worked, though he might now I changed the status to confirmed again.


Fix committed.

Upgraded.

---


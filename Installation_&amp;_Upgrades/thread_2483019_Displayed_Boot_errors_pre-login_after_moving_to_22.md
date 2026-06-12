---
title: "Displayed Boot errors pre-login after moving to 22.10"
date: 2023-01-17
forum: Installation &amp; Upgrades
---

### Post by waburden-4 on 2023-01-17
[COLOR=#000000][SIZE=2][FONT=arial]ERROR: Unable to locate IOAPIC for GSI 37[/FONT][/SIZE][/COLOR]
[FONT=arial][/FONT][SIZE=1][/SIZE][SIZE=2][FONT=arial]ERROR: Unable to locate IOAPIC for GSI 38[/FONT][/SIZE]
 
Started seeing this pre-login immediately after upgrading 22.04 to 22.10 along with a series of "blacklist: blacklisting hash (-13)" errors 
preceding the above. Everything seems to work fine, but why do I get that - it's annoying to be reminded of instability during each boot. 
As a former programmer, I find it rather unprofessional to allow this to persist after this much time. I've googled, but I only find 
really old issues and there seems to be no explanation or fix. If it will not cause future issues can I hide it from the display during 
bootups?

In case it matters, I have also reinstalled and updated 22.10 with the same result - indicating the kernal as source.

---

### Post by ActionParsnip on 2023-01-18
What is the output of
```

lsb_release -a; uname -a

```
Thanks

---

### Post by waburden-4 on 2023-01-20
Exactly as output:

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.10
Release:        22.10
Codename:       kinetic
Linux WAB-E6540 5.19.0-29-generic #30-Ubuntu SMP PREEMPT_DYNAMIC Wed Jan 4 12:14:09 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by waburden-4 on 2023-02-11
Hmmm... Ubuntu still reigns as the most popular LInux Distro, but after 3 weeks, the Ubuntu Community for all it's wealth of experience, still had nothing to offer this User?  Can't say I wasn't loyal - been with Ubuntu since 2005!  Guess moving my other devices to POP-OS was not such a bad strategy after all.

---

### Post by oldfred on 2023-02-11
What hardware?
Similar errors going back many years, but typically hardware related. 
More of a warning than a real error.

You may be able to suppress warning with noapic boot parameter.

[https://mjmwired.net/kernel/Documentation/kernel-parameters.txt](https://mjmwired.net/kernel/Documentation/kernel-parameters.txt)
> noapic		[SMP,APIC] Tells the kernel to not make use of any
[2630]("https://mjmwired.net/kernel/Documentation/kernel-parameters.txt#2630")				IOAPICs that may be present in the system.

Are you connecting to unusual devices, Windows NTFS or using Virtual Box

---

### Post by waburden-4 on 2023-02-12
Thank you for your response. I'll check into these suggestions. My hardware is a Dell Latitude E6540 (UEFI boot). I have used Dell Hardware for years as it's particularly LInux friendly! Had no issues like this in the past. As stated previously, this issue arose first on my upgrade to 22.10. No connections to any unusual devices. My only problematic connection to any device is my old HP Laserject 1020 which is job in itself with every upgrade - but that completely HP's issue and it's unwillingness to play nice with LInux. 

Other than these annoying boot messages, the hardware seems to work flawlessly with Ubuntu 22.10 and I quite like the new desktop changes! Stand by...

---

### Post by oldfred on 2023-02-12
I do not see your Dell model in fwupdate. Newer Dell systems are all available for update.
UEFI/BIOS updates brand model list  for Dell with (uefi >= 0.6.2 & dell >= 0.7.3) 
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

Do you have latest UEFI firmware from Dell that is available?

---

### Post by waburden-4 on 2023-05-10
Since this laptop is seldom used, I did not get around to trying any of the suggestions offered. I was kinda hoping Lunar Lobster would solve the problem but alas, no. The upgrade went flawlessly but the issue still persists. At this point i'd be happy just hiding the boot error messages rather than exploring firmware upgrades. Can you explain more about "suppressing the noapic boot parameter, previously mentioned. Do I edit grub in /etc/default and what's the syntax and position, for example?[COLOR=#000000]

[/COLOR]

---

### Post by tea for one on 2023-05-10
The suggestion in post 2 here [https://ubuntuforums.org/showthread.php?t=2477426](https://ubuntuforums.org/showthread.php?t=2477426) may help.
Example below
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="#0000FF"]loglevel=3[/COLOR]"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=true
```
Don't forget to run [COLOR="#0000FF"]sudo update-grub[/COLOR] after editing.

---

### Post by arp-101 on 2024-05-06
This is not a bug-fix. That is hiding the bug. loglevel=3 means only critical or fatal errors. 2 for warnings and 1 for Information. Finally 0 for debugging. I guess not everyone wants to hide that bug.

---

### Post by MAFoElffen on 2024-05-07
Welcome to Ubuntu Forums...

???

You know you woke this "year old" thread from the dead right? 22.10 isn't even support anymore.

---

### Post by coffeecat on 2024-05-07
Back to sleep, ancient, moribund thread.

*Thread closed*.

---


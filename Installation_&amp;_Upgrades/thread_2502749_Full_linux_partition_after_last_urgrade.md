---
title: "Full linux partition after last urgrade"
date: 2024-11-27
forum: Installation &amp; Upgrades
---

### Post by kopawel on 2024-11-27
After my last upgrade, around 1 month ago, my linux system partition is almost full....78Gb of data.
have no idea whats going on.

---

### Post by yancek on 2024-11-27
The image you posted shows the size of the partition as 75GB without 65GB used, about the same percentage as your various windows partitions.  That puts the partition at over 86% used and since the ext4 filesystem reserves 5% for itself, you're coming close to an unbootable system.  Move some of the data to another drive or remove it.

---

### Post by ActionParsnip on 2024-11-28
You can clear a lot of space by removing old kernels. What is the output of:
```

uname -a; echo; dpkg -l | grep linux-image | grep -v head

```

You may also want to run
```

sudo apt clean
sudo apt autoremove

```

---

### Post by wyattwhiteeagle on 2024-11-28
Not to interrupt here but the posted image shows a setup for dual booting.
It also shows that sda4 partition is either hidden or non-existant.

Wouldn't that also suggest that Windows is sharing files onto the Linux partitions?
That's not a problem, but it could help explain why the Linux partition is filling up this much and so quickly.

---

### Post by kopawel on 2024-11-28
[FONT=monospace][COLOR=#000000]running of sudo apt autoremove, removes around 9Mb of data only.

Output of [/COLOR][/FONT]uname -a; echo; dpkg -l | grep linux-image | grep -v head[FONT=monospace][COLOR=#000000] is.
Linux pawel-Aspire-5750G 6.8.0-49-generic #49-Ubuntu SMP PREEMPT_DYNAMIC Mon Nov  4 02:06:24 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux [/COLOR]

rc  linux-image-6.2.0-26-generic                             6.2.0-26.26~22.04.1                         amd64        Signed kernel image generic 
rc  linux-image-6.5.0-15-generic                             6.5.0-15.15~22.04.1                         amd64        Signed kernel image generic 
rc  linux-image-6.5.0-17-generic                             6.5.0-17.17~22.04.1                         amd64        Signed kernel image generic 
rc  linux-image-6.5.0-18-generic                             6.5.0-18.18~22.04.1                         amd64        Signed kernel image generic 
rc  linux-image-6.5.0-21-generic                             6.5.0-21.21~22.04.1                         amd64        Signed kernel image generic 
rc  linux-image-6.5.0-25-generic                             6.5.0-25.25~22.04.1                         amd64        Signed kernel image generic 
rc  linux-image-6.5.0-26-generic                             6.5.0-26.26~22.04.1                         amd64        Signed kernel image generic 
rc  linux-image-6.5.0-27-generic                             6.5.0-27.28~22.04.1                         amd64        Signed kernel image generic 
rc  linux-image-6.5.0-28-generic                             6.5.0-28.29~22.04.1                         amd64        Signed kernel image generic 
rc  linux-image-6.5.0-35-generic                             6.5.0-35.35~22.04.1                         amd64        Signed kernel image generic 
rc  linux-image-6.5.0-41-generic                             6.5.0-41.41~22.04.2                         amd64        Signed kernel image generic 
rc  linux-image-6.5.0-44-generic                             6.5.0-44.44~22.04.1                         amd64        Signed kernel image generic 
rc  linux-image-6.8.0-40-generic                             6.8.0-40.40                                 amd64        Signed kernel image generic 
rc  linux-image-6.8.0-45-generic                             6.8.0-45.45                                 amd64        Signed kernel image generic 
rc  linux-image-6.8.0-47-generic                             6.8.0-47.47                                 amd64        Signed kernel image generic 
ii  linux-image-6.8.0-48-generic                             6.8.0-48.48                                 amd64        Signed kernel image generic 
ii  linux-image-6.8.0-49-generic                             6.8.0-49.49                                 amd64        Signed kernel image generic 
ii  linux-image-generic                                      6.8.0-49.49                                 amd64        Generic Linux kernel
[/FONT]

---

### Post by ActionParsnip on 2024-11-28
> **kopawel said:**
> [FONT=monospace][COLOR=#000000]running of sudo apt autoremove, removes around 9Mb of data only.

Output of [/COLOR][/FONT]uname -a; echo; dpkg -l | grep linux-image | grep -v head[FONT=monospace][COLOR=#000000] is.
Linux pawel-Aspire-5750G 6.8.0-49-generic #49-Ubuntu SMP PREEMPT_DYNAMIC Mon Nov  4 02:06:24 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux [/COLOR]

rc  linux-image-6.2.0-26-generic                             6.2.0-26.26~22.04.1                         amd64        Signed kernel image generic 
rc  linux-image-6.5.0-15-generic                             6.5.0-15.15~22.04.1                         amd64        Signed kernel image generic 
rc  linux-image-6.5.0-17-generic                             6.5.0-17.17~22.04.1                         amd64        Signed kernel image generic 
rc  linux-image-6.5.0-18-generic                             6.5.0-18.18~22.04.1                         amd64        Signed kernel image generic 
rc  linux-image-6.5.0-21-generic                             6.5.0-21.21~22.04.1                         amd64        Signed kernel image generic 
rc  linux-image-6.5.0-25-generic                             6.5.0-25.25~22.04.1                         amd64        Signed kernel image generic 
rc  linux-image-6.5.0-26-generic                             6.5.0-26.26~22.04.1                         amd64        Signed kernel image generic 
rc  linux-image-6.5.0-27-generic                             6.5.0-27.28~22.04.1                         amd64        Signed kernel image generic 
rc  linux-image-6.5.0-28-generic                             6.5.0-28.29~22.04.1                         amd64        Signed kernel image generic 
rc  linux-image-6.5.0-35-generic                             6.5.0-35.35~22.04.1                         amd64        Signed kernel image generic 
rc  linux-image-6.5.0-41-generic                             6.5.0-41.41~22.04.2                         amd64        Signed kernel image generic 
rc  linux-image-6.5.0-44-generic                             6.5.0-44.44~22.04.1                         amd64        Signed kernel image generic 
rc  linux-image-6.8.0-40-generic                             6.8.0-40.40                                 amd64        Signed kernel image generic 
rc  linux-image-6.8.0-45-generic                             6.8.0-45.45                                 amd64        Signed kernel image generic 
rc  linux-image-6.8.0-47-generic                             6.8.0-47.47                                 amd64        Signed kernel image generic 
ii  linux-image-6.8.0-48-generic                             6.8.0-48.48                                 amd64        Signed kernel image generic 
ii  linux-image-6.8.0-49-generic                             6.8.0-49.49                                 amd64        Signed kernel image generic 
ii  linux-image-generic                                      6.8.0-49.49                                 amd64        Generic Linux kernel
[/FONT]

OK. You can clean up with:
```
 
sudo dpkg -P `dpkg -l | grep ^rc | awk {'print $2'}`

```

---

### Post by kopawel on 2024-11-28
exacly...there is a directory on linux partition, and it contains all windows partition files....around 40Gb[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294573&stc=1[/IMG]

---

### Post by kopawel on 2024-11-28
that didn't help at all, but thanks very much

size of files on that linux partition didn't change at all.


[FONT=monospace][COLOR=#54ff54]**pawel@pawel-Aspire-5750G**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo dpkg -P `dpkg -l | grep ^rc | awk {'print $2'}` [/COLOR]
(Odczytywanie bazy danych ... 247405 plików i katalogów obecnie zainstalowanych.) 
Czyszczenie z plików konfiguracyjnych pakietu libgtk-3-0:amd64 (3.24.33-1ubuntu2.2) ... 
Czyszczenie z plików konfiguracyjnych pakietu libmagic1:amd64 (1:5.41-3ubuntu0.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu libqt5core5a:amd64 (5.15.3+dfsg-2ubuntu0.2) ... 
Czyszczenie z plików konfiguracyjnych pakietu libqt5gui5:amd64 (5.15.3+dfsg-2ubuntu0.2) ... 
Czyszczenie z plików konfiguracyjnych pakietu libssl3:amd64 (3.0.2-0ubuntu1.18) ... 
Czyszczenie z plików konfiguracyjnych pakietu libssl3:i386 (3.0.2-0ubuntu1.18) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-image-6.2.0-26-generic (6.2.0-26.26~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-image-6.5.0-15-generic (6.5.0-15.15~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-image-6.5.0-17-generic (6.5.0-17.17~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-image-6.5.0-18-generic (6.5.0-18.18~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-image-6.5.0-21-generic (6.5.0-21.21~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-image-6.5.0-25-generic (6.5.0-25.25~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-image-6.5.0-26-generic (6.5.0-26.26~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-image-6.5.0-27-generic (6.5.0-27.28~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-image-6.5.0-28-generic (6.5.0-28.29~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-image-6.5.0-35-generic (6.5.0-35.35~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-image-6.5.0-41-generic (6.5.0-41.41~22.04.2) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-image-6.5.0-44-generic (6.5.0-44.44~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-image-6.8.0-40-generic (6.8.0-40.40) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-image-6.8.0-45-generic (6.8.0-45.45) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-image-6.8.0-47-generic (6.8.0-47.47) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-6.2.0-26-generic (6.2.0-26.26~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-6.5.0-15-generic (6.5.0-15.15~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-6.5.0-17-generic (6.5.0-17.17~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-6.5.0-18-generic (6.5.0-18.18~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-6.5.0-21-generic (6.5.0-21.21~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-6.5.0-25-generic (6.5.0-25.25~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-6.5.0-26-generic (6.5.0-26.26~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-6.5.0-27-generic (6.5.0-27.28~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-6.5.0-28-generic (6.5.0-28.29~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-6.5.0-35-generic (6.5.0-35.35~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-6.5.0-41-generic (6.5.0-41.41~22.04.2) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-6.5.0-44-generic (6.5.0-44.44~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-6.8.0-40-generic (6.8.0-40.40) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-6.8.0-45-generic (6.8.0-45.45) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-6.8.0-47-generic (6.8.0-47.47) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-extra-6.2.0-26-generic (6.2.0-26.26~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-extra-6.5.0-15-generic (6.5.0-15.15~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-extra-6.5.0-17-generic (6.5.0-17.17~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-extra-6.5.0-18-generic (6.5.0-18.18~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-extra-6.5.0-21-generic (6.5.0-21.21~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-extra-6.5.0-25-generic (6.5.0-25.25~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-extra-6.5.0-26-generic (6.5.0-26.26~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-extra-6.5.0-27-generic (6.5.0-27.28~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-extra-6.5.0-28-generic (6.5.0-28.29~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-extra-6.5.0-35-generic (6.5.0-35.35~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-extra-6.5.0-41-generic (6.5.0-41.41~22.04.2) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-extra-6.5.0-44-generic (6.5.0-44.44~22.04.1) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-extra-6.8.0-40-generic (6.8.0-40.40) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-extra-6.8.0-45-generic (6.8.0-45.45) ... 
Czyszczenie z plików konfiguracyjnych pakietu linux-modules-extra-6.8.0-47-generic (6.8.0-47.47) ... 
Czyszczenie z plików konfiguracyjnych pakietu mailcap (3.70+nmu1ubuntu1) ... 
Czyszczenie z plików konfiguracyjnych pakietu pipewire-media-session (0.4.1-2ubuntu1) ...



[/FONT]

---

### Post by kopawel on 2024-11-28
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294574&stc=1[/IMG]

---

### Post by yancek on 2024-11-28
Do you have entries in /etc/fstab for your various windows partitions?  You are not going to get rid of 40GB of data by removing kernels and current kernels are about 15MB.
The error in your dpkg entry says it " needs at least one package name argument" so that is not correct.  I don't know what you need to do in that case.

The directory you are referring to labelled 'none' is /dev/sda2 which is a windows partition.  Go to /media/pawel/ and find it and unmount it.  You can right click on the icon for it and select unmount.  After doing that check your / partition again.

You might get more help if you translated your output to English.

---

### Post by oldfred on 2024-11-28
It also looks like you have the old MBR(msdos) partitioning & sda4 then is the extended partition. It only acts as a container for all your logical partitions.
Also all partitions look like they have lots of data. Do you have good backups?

---

### Post by kopawel on 2024-11-29
Hi there. windows partition is unmounted but it doesn't changed anything.[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294576&stc=1[/IMG]


Thats fstab file:.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294577&stc=1[/IMG]

---

### Post by yancek on 2024-11-30
The image in your first post shows sda2 with a mount point of /none with size of 73.89 and used 39.70.  It shows sda3 as your Linux system partition and it shows size of 74.21 and used 65.76.  This same info shows in the image of post 7.  Your post 12 shows an image of partitions mounted/accessible under /media/pawel so it does not show the mount point none as that is mounted in the root of your filesystem per your earlier posts: ( /none).

What was the used amount prior to the update which now shows (65.76 for the / filesystem)?  What do you expect it to be?

---


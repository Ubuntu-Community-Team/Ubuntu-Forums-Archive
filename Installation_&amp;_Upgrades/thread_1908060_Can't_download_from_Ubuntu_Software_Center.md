---
title: "Can't download from Ubuntu Software Center"
date: 2012-01-12
forum: Installation &amp; Upgrades
---

### Post by KnaveOfHearts on 2012-01-12
Actually, this installation of Xubuntu 11.10 is only a few days old, and earlier I was able to download a package or two from the Software Center previously.  I am encountering different problems.

1.  The most common one is that I get the message "Filed to download package files. Check your Internet connections." If I try a second time, it complains about untrusted sources. 

2. On a couple occasions, there was no "Install" button. It said the software was unavailable (maybe not exactly what it said) from my sources.  After reading some postings, I ran the analyzer to select the best US source.  Same result, and same result too when I switched to the main repository.  After a few iterations of rebooting, restarting the app that accesses the Software Center, I was back in case 1.

Both 1 and 2 occur for ALL packages.  I was trying to download Libre Office.  I installed Dropbox, but I did it directly from their website, and the installation was weird.

The computer is an old Dell tower, which I thought I would recycle as a file server for rsync backups.  By way of background, I was unable to get Linux Mint to install on it.  Xubuntu installed, but without network connection.  It has wired network only.  I was able to get network working manually, and it was working fine throughout the above.  NetworkManager may be hosed--e.g., the resolv.conf file was empty except for a single line saying that it was created by NetworkManager.

Any help will be appreciated.

---

### Post by Old_Grey_Wolf on 2012-01-12
Open a terminal and copy these commands to the terminal command line ```
sudo apt-get update
``````
sudo apt-get upgrade
``` Execute them one at a time. You may be asked to enter your password. Then copy and past the output of those commands into a post in this thread. Please post the output between the ```

``` tags by clicking on the "#" icon.

I may be sleeping or at work when you reply; however, someone else should be able to help you.

---

### Post by KnaveOfHearts on 2012-01-13
[I]Thanks Old_Gray_Wolf!

[/I]It is hard to believe but I ran into a problem doing this.  I redirected the output of the update to a file, which worked fine, and I have that output.  Then I tried the same thing for the upgrade, but it called for a yes/no reply, so I stopped it and started over on that one, directly in a terminal window, after logging into this bulleting board using Firefox.  Then I opened an editor in order to copy and paste the saved update file.  That action of opening the editor immediately killed both my terminal window and my Firefox session on this site.  So what is below is the output from the first update but a second run of the upgrade.  I can say that the first upgrade run was mostly uneventful, with only some language libraries being listed.
[B]
sudo apt-get update[/B]:

```

Ign [http://linux.dropbox.com](http://linux.dropbox.com) oneiric InRelease
Get:1 [http://linux.dropbox.com](http://linux.dropbox.com) oneiric Release.gpg [489 B]
Get:2 [http://linux.dropbox.com](http://linux.dropbox.com) oneiric Release [2,603 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports InRelease
Get:3 [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main i386 Packages [782 B]
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security InRelease
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg [198 B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg [198 B]
Ign [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main TranslationIndex
Get:7 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release [9,759 B]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release.gpg [198 B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security Release.gpg [198 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release
Ign [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main Translation-en_US
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release [40.8 kB]
Ign [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main Translation-en
Get:11 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources [524 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security Release [40.8 kB]
Get:13 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages [593 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources [111 kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources [1,337 B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources [35.4 kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources [2,916 B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages [253 kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages [2,968 B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages [83.4 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [4,976 B]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex [74 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex [72 B]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex [71 B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex [73 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Sources
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe TranslationIndex
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/main Sources [23.1 kB]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/restricted Sources [14 B]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/universe Sources [8,189 B]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/multiverse Sources [653 B]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/main i386 Packages [65.2 kB]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/restricted i386 Packages [14 B]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/universe i386 Packages [22.2 kB]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/multiverse i386 Packages [1,653 B]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/main TranslationIndex [73 B]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/multiverse TranslationIndex [71 B]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/restricted TranslationIndex [70 B]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/universe TranslationIndex [73 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en [118 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Translation-en
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/main Translation-en [34.5 kB]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/multiverse Translation-en [840 B]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/restricted Translation-en [14 B]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/universe Translation-en [16.0 kB]
Fetched 883 kB in 5s (152 kB/s)
Reading package lists...

```[B]

sudo apt-get upgrade[/B]:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by KnaveOfHearts on 2012-01-13
After running the update and upgrade (see my previous post), I was able to download LibreOffice from the Ubuntu Software Center. Was that expected?

---

### Post by IWantFroyo on 2012-01-13
Usually you shouldn't have problems downloading programs as long as long as you have a connection, but it's always a good idea to refresh your database (apt-get update) before installing apps.
What bugs me is that he Update Manager is supposed to run that command for you.
Anyways, that's not really that strange. Arch Linux flat-out refuses to install packages unless you update. Errors every time.

---

### Post by Old_Grey_Wolf on 2012-01-13
> **KnaveOfHearts said:**
> After running the update and upgrade (see my previous post), I was able to download LibreOffice from the Ubuntu Software Center. Was that expected?

I'm glad it is working for you now.

I had actually expected to see some errors telling me what was causing your original problem; such as, malformed line in the sources.list file, or a previous partial update that was preventing the upgrade from working.

Entering "sudo apt-get update" may have fixed the problem; therefore, there were no errors reported.

Just use the computer as usual, and post again if the problem reoccurs in the future.

---

### Post by Old_Grey_Wolf on 2012-01-13
If you are currently not having problems, please mark this thread a solved.

If you do not know how to do that, near the top of the webpage (scroll up) there is a menu "Thread Tools". Select "Mark this thread as solved". It lets other people searching the forums know that this had a working solution and they don't need to provide additional help.

Thank you.

---


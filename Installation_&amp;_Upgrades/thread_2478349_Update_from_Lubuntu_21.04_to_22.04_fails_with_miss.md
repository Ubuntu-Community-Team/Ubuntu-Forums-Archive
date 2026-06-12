---
title: "Update from Lubuntu 21.04 to 22.04 fails with missing debs"
date: 2022-08-24
forum: Installation &amp; Upgrades
---

### Post by maxim-vekslers on 2022-08-24
Hey gusy,

Trying to upgrade fails with missing debs [https://paste.ubuntu.com/p/RJBFm6wrVY/](https://paste.ubuntu.com/p/RJBFm6wrVY/)

Any ideas what could be done about that?

---

### Post by QIII on 2022-08-24
The first two things I would try before digging very far would be: 

1.  The mirror may be being updated or you might be encountering connectivity issues.   Wait an hour or two and try again.

2.  Change the mirror in your package manager and try again.

---

### Post by maxim-vekslers on 2022-08-24
Solved it by finding a source that works

[https://repo.miserver.it.umich.edu/ubuntu/pool/main/](https://repo.miserver.it.umich.edu/ubuntu/pool/main/)

And then download all the missing files manually

[FONT=monospace][COLOR=#000000]`
for f in `cat /tmp/http.txt  | grep http | sed 's/il.archive.ubuntu.com/repo.miserver.it.umich.edu/'`; do wget $f; done
[/COLOR][/FONT][FONT=monospace][COLOR=#000000]cd /var/cache/apt/archives/[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]sudo mv ~/Downloads/*deb .[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]`
[/COLOR]
[/FONT]

---

### Post by guiverc on 2022-08-24
I picked a package in your provide paste and I see it available, ie.

```
 libnss-nisplus | 1.3-0ubuntu6 | jammy   | source, amd64, arm64, armhf, i386, ppc64el, riscv64, s390x

```

The obvious anyway...

Lubuntu 21.04 was a mid-development cycle release (ie.* 20.10, 21.04, 21.10 before the final 22.04 LTS release* *make up the full development cycle; three non-LTS before final LTS product*), thus it had only one *fully supported* and *Quality Assurance* tested upgrade path; to the next release or Lubuntu 21.10

I assume you read the upgrade instructions, marked the packages that were removed from seeds, but want to keep as *manually installed* so they won't be removed during the *release-upgrade* process, and made other required changes so any altered *openbox* etc config changes survived as per documentation.  We only QA tested upgrades from 21.10 to 22.04, or 20.04 to 22.04 so you may experience issues beyond what we documented in [release notes]("https://lubuntu.me/jammy-1-released/") & upgrade instructions due to your choice of using an *unsupported* upgrade path.

From your paste though, I agree with QIII.

---

### Post by maxim-vekslers on 2022-08-24
Thanks for the quick reply QIII, the problem keeps reapearing [https://askubuntu.com/questions/1423608/cant-upgrade-to-ubuntu-22-404-not-found](https://askubuntu.com/questions/1423608/cant-upgrade-to-ubuntu-22-404-not-found)

Also for me, with other packages 

`
[FONT=monospace][COLOR=#000000]Fetching[/COLOR]
Err [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) jammy/main i386 libcrypt1 i386 1:4.4.27-1                                                                                                                                                                                                                                           
  404  Not Found [IP: 192.115.211.70 80]                                                                                                                                                                                                                                                                                    
Fetched 0 B in 0s (0 B/s)                                                                                                                                                                                                                                                                                                   
Err [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) jammy/main i386 libcrypt1 i386 1:4.4.27-1                                                                                                                                                                                                                                           
  404  Not Found [IP: 192.115.211.70 80]                                                                                                                                                                                                                                                                                    
Fetched 0 B in 0s (0 B/s)                                                                                                                                                                                                                                                                                                   
Err [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) jammy/main i386 libcrypt1 i386 1:4.4.27-1                                                                                                                                                                                                                                           
  404  Not Found [IP: 192.115.211.70 80]                                                                                                                                                                                                                                                                                    
Fetched 0 B in 0s (0 B/s)                                                                                                                                                                                                                                                                                                  
`

How do you change the mirror from command line? 

I'm getting with apt-mirror-updater


```
[/FONT][FONT=monospace][COLOR=#54FF54]**m@m-inspiron5567**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~/Downloads**[/COLOR][COLOR=#000000]$ apt-mirror-updater -l[/COLOR]
[COLOR=#18B218]2022-08-24 09:01:13[/COLOR][COLOR=#000000] [/COLOR][COLOR=#B218B2]m-inspiron5567[/COLOR][COLOR=#000000] [/COLOR][COLOR=#1818B2]apt_mirror_updater[2599973][/COLOR][COLOR=#000000] [/COLOR][COLOR=#686868]**INFO**[/COLOR][COLOR=#000000] Release Ubuntu 21.04 (hirsute) based on Ubuntu 21.04 is EOL, checking if it has been archived ..[/COLOR]
[COLOR=#18B218]2022-08-24 09:01:13[/COLOR][COLOR=#000000] [/COLOR][COLOR=#B218B2]m-inspiron5567[/COLOR][COLOR=#000000] [/COLOR][COLOR=#1818B2]apt_mirror_updater[2599973][/COLOR][COLOR=#000000] [/COLOR][COLOR=#686868]**INFO**[/COLOR][COLOR=#000000] Checking if Ubuntu 21.04 (hirsute) based on Ubuntu 21.04 is available on [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) ..[/COLOR]
[COLOR=#18B218]2022-08-24 09:01:13[/COLOR][COLOR=#000000] [/COLOR][COLOR=#B218B2]m-inspiron5567[/COLOR][COLOR=#000000] [/COLOR][COLOR=#1818B2]apt_mirror_updater[2599973][/COLOR][COLOR=#000000] [/COLOR][COLOR=#686868]**INFO**[/COLOR][COLOR=#000000] Confirmed that release Ubuntu 21.04 (hirsute) based on Ubuntu 21.04 has been archived.[/COLOR]
[COLOR=#18B218]2022-08-24 09:01:13[/COLOR][COLOR=#000000] [/COLOR][COLOR=#B218B2]m-inspiron5567[/COLOR][COLOR=#000000] [/COLOR][COLOR=#1818B2]apt_mirror_updater[2599973][/COLOR][COLOR=#000000] [/COLOR][COLOR=#686868]**INFO**[/COLOR][COLOR=#000000] Checking 1 mirror for availability and performance ..[/COLOR]
[COLOR=#18B218]2022-08-24 09:01:14[/COLOR][COLOR=#000000] [/COLOR][COLOR=#B218B2]m-inspiron5567[/COLOR][COLOR=#000000] [/COLOR][COLOR=#1818B2]apt_mirror_updater[2599973][/COLOR][COLOR=#000000] [/COLOR][COLOR=#686868]**INFO**[/COLOR][COLOR=#000000] Checking 1 mirror for Archive-Update-in-Progress marker ..[/COLOR]
[COLOR=#18B218]2022-08-24 09:01:14[/COLOR][COLOR=#000000] [/COLOR][COLOR=#B218B2]m-inspiron5567[/COLOR][COLOR=#000000] [/COLOR][COLOR=#1818B2]apt_mirror_updater[2599973][/COLOR][COLOR=#000000] [/COLOR][COLOR=#686868]**INFO**[/COLOR][COLOR=#000000] Finished checking 1 mirror (took 1.33 seconds).[/COLOR]
-------------------------------------------------------------------------------------
| [COLOR=#54FF54]**Rank**[/COLOR][COLOR=#000000] | [/COLOR][COLOR=#54FF54]**Mirror URL**[/COLOR][COLOR=#000000]                            | [/COLOR][COLOR=#54FF54]**Available?**[/COLOR][COLOR=#000000] | [/COLOR][COLOR=#54FF54]**Updating?**[/COLOR][COLOR=#000000] | [/COLOR][COLOR=#54FF54]**Bandwidth**[/COLOR][COLOR=#000000] |[/COLOR]
-------------------------------------------------------------------------------------
|    1 | [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) | Yes        | No        | 2.42 KB/s |
-------------------------------------------------------------------------------------
```[/FONT]

---

### Post by maxim-vekslers on 2022-08-24
> **guiverc said:**
> I picked a package in your provide paste and I see it available, ie.

```
 libnss-nisplus | 1.3-0ubuntu6 | jammy   | source, amd64, arm64, armhf, i386, ppc64el, riscv64, s390x

```

The obvious anyway...

Lubuntu 21.04 was a mid-development cycle release (ie.* 20.10, 21.04, 21.10 before the final 22.04 LTS release* *make up the full development cycle; three non-LTS before final LTS product*), thus it had only one *fully supported* and *Quality Assurance* tested upgrade path; to the next release or Lubuntu 21.10

I assume you read the upgrade instructions, marked the packages that were removed from seeds, but want to keep as *manually installed* so they won't be removed during the *release-upgrade* process, and made other required changes so any altered *openbox* etc config changes survived as per documentation.  We only QA tested upgrades from 21.10 to 22.04, or 20.04 to 22.04 so you may experience issues beyond what we documented in [release notes]("https://lubuntu.me/jammy-1-released/") & upgrade instructions due to your choice of using an *unsupported* upgrade path.

From your paste though, I agree with QIII.

Ha, I did not do any of that. 

Let me take a look...

---

### Post by maxim-vekslers on 2022-08-24
[guiverc]("https://ubuntuforums.org/member.php?u=2074246") I can't find the mentioned steps in the upgrade link you've published. I did not mark packages for suvrival, I'm fine with the defaults as they would ship with the new release. Same goes for openbox configuraitons.

I'm actually running KDE most of the times on top of Lubuntu package selections.

I think that my main problem (except from the fact that the upgrade path from 20.04 to 22.04 as I understand is less tested {fingers corssed}) is that the default mirror being selected by apt for me is the IL mirror, which seesm to be experiecing problems (not for the 1st time).

Any way to override the mirroring source selection logic to provide it a differet mirror?

---

### Post by maxim-vekslers on 2022-08-24
Progress

Applied a random apt-mirror-updater source:

```
[COLOR=#002D7A !important][FONT=Monaco]apt[/FONT][/COLOR][COLOR=#006FE0 !important][FONT=Monaco]-[/FONT][/COLOR][COLOR=#002D7A !important][FONT=Monaco]mirror[/FONT][/COLOR][COLOR=#006FE0 !important][FONT=Monaco]-[/FONT][/COLOR][COLOR=#002D7A !important][FONT=Monaco]updater[/FONT][/COLOR][COLOR=#006FE0 !important][FONT=Monaco] [/FONT][/COLOR][COLOR=#006FE0 !important][FONT=Monaco]-[/FONT][/COLOR][COLOR=#000000][FONT=Monaco]c[/FONT][/COLOR][COLOR=#006FE0 !important][FONT=Monaco] [/FONT][/COLOR][COLOR=#002D7A !important][FONT=Monaco]http[/FONT][/COLOR][COLOR=#006FE0 !important][FONT=Monaco]:[/FONT][/COLOR][COLOR=#006FE0 !important][FONT=Monaco]/[/FONT][/COLOR][COLOR=#006FE0 !important][FONT=Monaco]/[/FONT][/COLOR][COLOR=#002D7A !important][FONT=Monaco]th[/FONT][/COLOR][COLOR=#004ED0 !important][FONT=Monaco].archive[/FONT][/COLOR][COLOR=#004ED0 !important][FONT=Monaco].ubuntu[/FONT][/COLOR][COLOR=#004ED0 !important][FONT=Monaco].com[/FONT][/COLOR][COLOR=#006FE0 !important][FONT=Monaco]/[/FONT][/COLOR][COLOR=#002D7A !important][FONT=Monaco]ubuntu[/FONT][/COLOR][COLOR=#006FE0 !important][FONT=Monaco]/
```

[/FONT][/COLOR]And restarted the upgrade:

[FONT=monospace][COLOR=#000000]sudo do-release-upgrade -m desktop


The process seems to be working now :)



[/COLOR][/FONT][FONT=courier new][COLOR=#000000]Do you want to start the upgrade?  [/COLOR]


18 packages are going to be removed. 200 new packages are going to be  
installed. 2328 packages are going to be upgraded.  

You have to download a total of 97.2 k. This download will take about  
1 second with your connection.  

Installing the upgrade can take several hours. Once the download has  
finished, the process cannot be canceled.  

 Continue [yN]  Details [d]y

Fetching
Get:1 [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) jammy/main i386 libcrypt1 i386 1:4.4.27-1 [97.2 kB]                                                                                                                                                                                                                               
Fetched 97.2 kB in 0s (0 B/s)                                                                                                                                                                                                                                                                                               

Upgrading
Fetched 0 B in 0s (0 B/s)                                                                                                                                                                                                                                                                                                   
  MarkInstall libc6:amd64 < 2.33-0ubuntu5 -> 2.35-0ubuntu3.1 @ii umU NPb Ib > FU=1
    MarkInstall locales:amd64 < 2.33-0ubuntu5 -> 2.35-0ubuntu3.1 @ii umU Ib > FU=0
    Installing libc-bin:amd64 as Depends of locales:amd64
      MarkInstall libc-bin:amd64 < 2.33-0ubuntu5 -> 2.35-0ubuntu3.1 @ii umU > FU=0
    MarkInstall libc6:i386 < 2.33-0ubuntu5 -> 2.35-0ubuntu3.1 @ii umU > FU=0
  ignore old unsatisfied important dependency on libnss-nis:amd64
  ignore old unsatisfied important dependency on libnss-nisplus:amd64
Starting pkgProblemResolver with broken count: 0
Starting 2 pkgProblemResolver with broken count: 0
Done

Upgrading
Fetched 0 B in 0s (0 B/s)                                                                                                                                                                                                                                                                                                   
Preconfiguring packages ...
Preconfiguring packages ...
Preconfiguring packages ...
(Reading database ... 304652 files and directories currently installed.)
Preparing to unpack .../locales_2.35-0ubuntu3.1_all.deb ...
Unpacking locales (2.35-0ubuntu3.1) over (2.33-0ubuntu5) ...

Progress: [  6%]
Preparing to unpack .../libc6_2.35-0ubuntu3.1_amd64.deb ...
De-configuring libc6:i386 (2.33-0ubuntu5) ...
Checking for services that may need to be restarted...
Checking init scripts...
Checking for services that may need to be restarted...
Checking init scripts...
Stopping some services possibly affected by the upgrade (will be restarted later):
  cron: stopping...done.

Unpacking libc6:amd64 (2.35-0ubuntu3.1) over (2.33-0ubuntu5) ...

Progress: [ 12%]
Preparing to unpack .../libc6_2.35-0ubuntu3.1_i386.deb ...

[/FONT][FONT=monospace]
[/FONT]

---

### Post by maxim-vekslers on 2022-08-24
Happy to update the the version upgrade worked!

---

### Post by guiverc on 2022-08-24
> **maxim-vekslers said:**
> [guiverc]("https://ubuntuforums.org/member.php?u=2074246") I can't find the mentioned steps in the upgrade link you've published. I did not mark packages for suvrival, I'm fine with the defaults as they would ship with the new release. Same goes for openbox configuraitons.

I'm actually running KDE most of the times on top of Lubuntu package selections.

I think that my main problem (except from the fact that the upgrade path from 20.04 to 22.04 as I understand is less tested {fingers corssed}) is that the default mirror being selected by apt for me is the IL mirror, which seesm to be experiecing problems (not for the 1st time).

Any way to override the mirroring source selection logic to provide it a differet mirror?

If your box is online, your countries mirror of the main archive site is used instead, but if you're offline the main archive will be used. You can use any mirror though that's listed - [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

> I can't find the mentioned steps in the upgrade link you've published

I'm not sure what you're referring to here, but

- our upgrade instructions are found in the manual - [https://manual.lubuntu.me/stable/D/upgrading.html](https://manual.lubuntu.me/stable/D/upgrading.html)

(*current manuals are stable for 22.04 & lts still shows 20.04, which I'd expect to change just prior to Lubuntu 22.10's release or our first release in our working towards our next LTS in this current development cycle*).

- the dropped packages (apps/programs) were mentioned in the release notes; ie. seeds no longer include them so they don't appear on new installs, but existing users who may have used them were directed in the release notes to this page- [https://discourse.lubuntu.me/t/dropping-trojita-k3b-fcitx-from-lubuntu-jammy-22-04-seed/3044](https://discourse.lubuntu.me/t/dropping-trojita-k3b-fcitx-from-lubuntu-jammy-22-04-seed/3044) so they can mark the packages as *manually installed* so they won't be removed during *release-upgrade* or *re-install* process.

Both paths
- from 21.10 or the prior release in the cycle, and
- from 20.04 or the prior LTS release from the prior cycle
got tested equally (CI + full QA).  Most users upgrade LTS to LTS.

21.04 gets only some CI package testing to 22.04 as that's not supported for any Ubuntu product (Ubuntu, Kubuntu, Lubuntu or any), 20.04 to 21.04 is actually *supported* and thus tested for (*by main Ubuntu, not by flavors though*), ie. from LTS to next non-LTS, but not non-LTS skipping to next LTS.
The upgrade path from 21.10 to 22.04 opened shortly after 22.04 was released; as that *jump* is minor & problems are don't expect.. The upgrade from 20.04 to 22.04 however didn't open until ***after*** the release of 22.04.1 as that's a *large* *jump* as it moves users from one *full development cycle* to the next (*covering two years of development*), thus the delay of the upgrade opening for months.  You opted for a non-QA tested upgrade path by not using *supported* upgrade paths.

FYI:  I keep releases of all *supported* Lubuntu products, when 21.04 reached EOL, as I didn't need a 21.10 system (*already had one*), I used the box as a QA-test install (*install using existing partition**, or what I prefer calling upgrade via re-install*) and that install became a *jammy* (or what now is 22.04) system, no data loss, & all my *manually installed* packages got auto-reinstalled  (ie. QA-tested the non-destructive re-install procedure).  I actually don't upgrade those re-installs, but weekly re-install them, and post-install ensure (a) no data is lost, (b) my *manually installed* packages were re-installed automatically and it achieves the upgrade of packages given I use the *daily* ISO for my re-install thus achieve a upgrade of packages & QA-test of an install as ~quickly asupgrading packages takes anyway.  That is likely what I'd have done to *skip* releases... it works for all Ubuntu Desktop (*and flavor*) systems, though as system directories are wiped, server configs/conf files can get lost as it's a desktop intended re-install procedure.

---


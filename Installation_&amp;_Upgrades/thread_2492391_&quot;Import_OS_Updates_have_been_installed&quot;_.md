---
title: "&quot;Import OS Updates have been installed&quot; notification won't go away at log in"
date: 2023-11-09
forum: Installation &amp; Upgrades
---

### Post by mrgou on 2023-11-09
I upgraded to Ubuntu 23.10 and, after a firmware update, I keep having an "Important OS Updates..." notification showing at every log in. I keep dismissing it, but it still shows up every time I log in.

I tried disabling notifications entirely in the settings for several applications (Ubuntu Software, Snap Store, Portal, Snapd User Session Agent, Evolution alarm) without success. I also read [here]("https://askubuntu.com/questions/1469200/how-can-i-dismiss-software-updates-installed-notification") that I could remove the file /var/lib/PackageKit/offline-update-completed, but there is no such file. With locate, I also tried to find any other file with completed in its name, but found nothing relevant.

It's not a big deal, but it's getting really annoying.

Any idea?

---

### Post by MAFoElffen on 2023-11-09
can you post exactly what it is saying and when? What are the conditions? Desktop or Server? If Desktop... Is it from the Notifications next to calendar in the top bar?

---

### Post by mrgou on 2023-11-10
The message exactly says "Import OS Updates have been installed", and it appears in the gnome notification area in the top bar when logging in. It's really a regular, common notification, except it's not supposed to persist this way.

---

### Post by MAFoElffen on 2023-11-10
Do this:
```

apt list gnome-software
snap list snap-store 

```
I see a recent discussion, where if both of those are installed at the same time, each has it's own tracker to keep track of updates and notations, where they conflict and then have this persistent notification problem... Users in that discussion reported that if they uninstalled one or the other of those two, so that only one remained, that it went away...

---

### Post by mrgou on 2023-11-11
gnome-software is not installed. Only snap-store is...

---

### Post by MAFoElffen on 2023-11-11
And what happens if you do 
```

sudo snap refresh

```

---

### Post by mrgou on 2023-11-12
I do that every day, along with sudo apt full-upgrade... :-( At this point, I'm just hoping that, some day, another notification will simply overwrite that one and go away.

---

### Post by MAFoElffen on 2023-11-12
LOL. Yup. Maybe file a bug on it to see if there is a problem somewhere they haven't noticed yet.

---

### Post by philhughes on 2023-11-12
I also was getting this. After trying various things to no avail, I realised that on that PC, I still had the "Ubuntu Software" app installed, not the new flutter-based "App Center". After some searching, I found the bug report below [1], and it appears to be related to this.

If you see the "Ubuntu Software" app installed, then it appears that you likely have the wrong version of the snap-store installed. You can check with:

```
$ snap info snap-store
[snip]
snap-id:      gjf3IPXoRiipCu9K0kVu52f0H56fIksg
tracking:     latest/stable
refresh-date: 2023-04-30
channels:
  latest/stable:     41.3-71-g709398e 2023-04-28  (959) 12MB -
  latest/candidate:  41.3-76-g2e8f3b0 2023-10-12 (1058) 12MB -
  latest/beta:       &#8593;                                       
  latest/edge:       0+git.3de38a7    2023-11-10 (1067) 10MB -
  preview/stable:    –                                       
  preview/candidate: 0.2.7-alpha      2023-02-02  (864) 10MB -
  preview/beta:      &#8593;                                       
  preview/edge:      0.3.0-alpha      2023-08-14 (1017) 11MB -
installed:           41.3-71-g709398e             (959) 12MB -
```

Note the "tracking" entry. On another PC that had the App Centre installed:

```
$ snap info snap-store
[snip]
snap-id:      gjf3IPXoRiipCu9K0kVu52f0H56fIksg
tracking:     latest/stable/ubuntu-23.10
refresh-date: 33 days ago, at 12:36 BST
channels:
  latest/stable:     41.3-71-g709398e 2023-04-28  (959) 12MB -
  latest/candidate:  41.3-76-g2e8f3b0 2023-10-12 (1058) 12MB -
  latest/beta:       &#8593;                                       
  latest/edge:       0+git.3de38a7    2023-11-10 (1067) 10MB -
  preview/stable:    –                                       
  preview/candidate: 0.2.7-alpha      2023-02-02  (864) 10MB -
  preview/beta:      &#8593;                                       
  preview/edge:      0.3.0-alpha      2023-08-14 (1017) 11MB -
installed:           0+git.e118b05               (1046) 11MB -
```

I changed the snap-store on the affected PC to track channel latest/stable/ubuntu-23.10. The App Centre was now installed and this got rid of the repeated notification. It seems strange however that the installed version is not the version shown by latest/stable.

```
$ killall snap-store
$ sudo snap refresh snap-store --channel=latest/stable/ubuntu-23.10
```

I guess that means that all of the other snaps are tracking the wrong channel, though I haven't yet changed channel for the others. Someone in the bug report has asked that question, but received no answer.

[1] [https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/2036765](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/2036765)

---

### Post by Dennis N on 2023-11-12
The **App Center** only manages Snaps at this time. So, if you want to manage .deb packages too, you want Ubuntu Software instead which tracks **latest/stable** (without the ubuntu-23.10).

Some further information:
My new installation of Ubuntu 23.10 had the App Center only. What I did was to install gnome-software in addition. That combination is working fine.

_Correction_:
Further checking shows how to get .deb packages. After search, you need to "filter results" for Debian packages. If you don't do this, you only see snaps which is the default setting.

---

### Post by mrgou on 2023-11-12
> I changed the snap-store on the affected PC to track channel  latest/stable/ubuntu-23.10. The App Centre was now installed and this  got rid of the repeated notification. It seems strange however that the  installed version is not the version shown by latest/stable.

Yes, that's it! Running the suggested commands did the trick! Thank you!!!

---

### Post by philhughes on 2023-11-12
Thanks for the extra information Dennis N.

The whole situation is very confusing. The release notes say "There is a brand new Ubuntu App Center that replaces the previous Snap Store. The application has been written from scratch using the Flutter toolkit." Unless I've missed it, there is no mention that it doesn't manage debs.

Out of 5 PCs I know of running 23.10, two have the App Center installed but not Ubuntu Software. One of these was a fresh install, one an upgrade. The other three have Ubuntu Software but not the App Center. All of these were upgrades.

---

### Post by Dennis N on 2023-11-12
> Unless I've missed it, there is no mention that it doesn't manage debs.
You will see when you look for something to install and want a .deb package. There are currently snap versions only. In time, it should manage .deb packages also. 

The App Center version I have matches yours:
```
dmn@Tyana-vm:~$ snap list | grep snap-store
snap-store                 0+git.e118b05    1046   latest/stable/&#8230;  canonical**  -

```
The App Center "About" tells us it is an alpha version - something early in the development stage.

_Correction_:
Further checking shows how to get .deb packages. After search, you need to "filter results" for Debian packages. If you don't do this, you only see snaps which is the default setting.

---

### Post by mrgou on 2023-11-13
Yes, sudo snap refresh snap-store --channel=latest/stable/ubuntu-23.10 did it, thank you!

---

### Post by bonzini on 2023-11-18
This suggested fix:

```
$ killall snap-store
$ sudo snap refresh snap-store --channel=latest/stable/ubuntu-23.10
```

worked for me; thank you very much, also for the Launchpad link.

---

### Post by mrgou on 2023-11-26
The problem is occurring again. I ran again sudo snap refresh snap-store --channel=latest/stable/ubuntu-23.10, but it just responded that no update was available, and it didn't prevent the notification from showing up again at each log in... I guess this must be a bug in snap-store.

---

### Post by bonzini on 2023-11-26
Same problem here.  This morning (26 November 2023) when I booted and logged in, there was that !($&!($!@ message again!

Tracking remains at latest/stable/ubuntu-23.10.

In my case the update indicated is always UEFI dbx and I don't seem to be able to run down any fixes related to that either.  In particular my /boot configuration looks up to date / OK / no old junk floating around there that I can see.

---

### Post by artunix on 2023-12-30
this worked for me; got rid of the '_brown_' shopping bag and kept the '_white_' shopping bag, no more notice!!!!
sudo snap remove snap-store

spread it around; thick!!

---


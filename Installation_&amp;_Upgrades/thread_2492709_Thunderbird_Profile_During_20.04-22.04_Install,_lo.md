---
title: "Thunderbird Profile During 20.04-22.04 Install, lost email"
date: 2023-11-20
forum: Installation &amp; Upgrades
---

### Post by darklord-dr on 2023-11-20
Been using Ubuntu for years.  Recently installed UbuntuStudio 22.04 on 2nd OS Partition of external USB HD.  /home resides on another partition specifically created to avoid data loss during upgrades/installs.  I had recently backed up entire HD to another external HD, though not immediately prior to install. I think I've had a few weeks of email downloaded since backup.  Don't recall the email details except that I was setup to download email from my ISP's email server to my local drive upon connection.  Upon initial use of Thunderbird on newly installed 22.04, I was surprised to find my local email directory structure missing, along w/ it's content.  The new Thunderbird is at 115.4.1.  I don't recall reading anything about steps to preserve Thunderbird email in the installation notes I had read.  I gather Thunderbird replaced my ~/.thunderbird  directory structure.  Wondering now how I go about merging the old and new email and directory structures, and what other gotcha's await as I begin using the other apps w/ data in /home.

Did I select the wrong option when installing Ubuntu as to reusing /home?  Should there have been a better description of the installation option?

Appreciate any time and effort anyone may give me on the matter.  After composing above I'm now thinking perhaps a Thunderbird forum would have been a better choice, though the heads-up to Ubuntu installers is also worthwhile.

Thank you.

---

### Post by TheFu on 2023-11-20
Before doing anything major, like replacing an OS, certainly you've seen people strongly suggest backing up anything you don't want to lose, right?

Because we weren't there watching your install choices, we don't know what you may have done wrong, if anything.  If everything else in your HOME was lost too, then I suspect it was a checkbox in the disk setup that say "Format Partition" or "format file system" - something like that.

OTOH, if other things are still there, perhaps the Thunderbird files are too.   In 22.04, didn't Thunderbird switch from being a .deb package to being a snap package?  Snaps store data in a different place.  I specifically switched off Ubuntu desktops to avoid the snap fiasco that has taken hold inside Canonical, so I don't know, but I'd be surprised if there wasn't a method to import all the old Thunderbird profile/data into a snap area for use.  That would be the line of questions I'd trace.  [https://forum.snapcraft.io/t/thunderbird-and-local-folder/31976](https://forum.snapcraft.io/t/thunderbird-and-local-folder/31976) has the same question, but no answer I see.
[https://discourse.ubuntu.com/t/thunderbird-snap/19156/13](https://discourse.ubuntu.com/t/thunderbird-snap/19156/13) is another.

---

### Post by darklord-dr on 2023-11-20
I definitely would not have checked anything that suggested reformatting the /home partition or file system.  Thunderbird appears to have been sourced from .deb, and would have been part of UbuntuStudio distribution.  I don't recall the exact verbiage, but I do recall a check box referring to "/home", I think it referred to "reusing /home", which I interpreted to mean that the install would not create a fresh /home tree.  I did back up the drive weeks ago, believing the point of a separate /home partition was to protect it from OS installs/upgrades, and protect '/' from being filled by "user" activity.  This is a one-user home system.  However, lesson learned as to the immediacy and scope of backup.  At this point, I believe the Ubuntu install blitzed my /home directory, and I have to believe that in so doing if it was due to a user selectable option, that that option was unaccompanied by adequate clarity as to the function about to be performed.  I thank you for your input.  I encourage the packagers/coders of the install package to revisit any such option presentation and/or related processing.  This install was from the UbuntuStudio 22.04 Live USB.  I suspect the "Studio" portion has nothing to do with it.

[FONT=monospace][COLOR=#000000]apt policy thunderbird [/COLOR]
thunderbird: 
  Installed: 1:115.4.1+build1-0ubuntu0.22.04.1 
  Candidate: 1:115.4.1+build1-0ubuntu0.22.04.1 
  Version table: 
 *** 1:115.4.1+build1-0ubuntu0.22.04.1 500 
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 Packages 
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/main amd64 Packages 
        100 /var/lib/dpkg/status 
     1:91.8.0+build2-0ubuntu1 500 
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
[/FONT]

---

### Post by darklord-dr on 2023-11-20
Clarification, my /home directory structure was NOT entirely blitzed.  So far, normal "user" files appear to be intact, with only the "."-hidden portion of the tree having been affected.  I think I'll restore the other elements of that tree from my backup before re-installing their related packages and see what happens upon each initial instantiation.

I think my email is the only portion of the /home path that would have suffered significant loss in this event.

---

### Post by darklord-dr on 2023-11-20
Update:  I've since discovered the following new directory in my /home directory:  "dotfiles_backup_2023-11-12_11-35-04".  I did not create this.  I'm thinking this was created during Ubuntu install.  I've seen no reference to this in the install doc I've reviewed to now.  Maybe God does look out for little children and fools.

---

### Post by ajgreeny on 2023-11-21
See what is in the hidden .thunderbird folder in your home and you may find there are more than one profile folders, ie, those named <alphanumeric>.default or similar name.

You can start thunderbird using command```
thunderbird -p
``` which will offer profiles that still exist.
Try them one by one and you may find the old one is there with all you emails that you want.

---

### Post by darklord-dr on 2023-11-22
I only briefly reviewed that "dotfiles_backup_2023-11-12_11-35-04" folder prior to my last post.  I was falling asleep on myself and opted for bed, but I am pretty confident that it holds all my email history for which I was concerned, from its sheer size.  I'll be researching the process to merge that history w/ my new "profile".  I'm certainly thankful that the Ubuntu team saved me from my shortcomings, but I do believe this mechanism should have been documented in related installation documentation including the "merge" process or at least pointing to it.  Again, thank you for your input.  I intend to document what I learn and post it here for posterity.

---

### Post by ActionParsnip on 2023-11-23
Check ownership of your $HOME is all assigned to your user. If the files are not owned by your user then they can't be read and will show no email. You can check the files in
```

$HOME/.mozilla

```
and below. make sure they are owned by your username

---

### Post by darklord-dr on 2023-11-23
Thank you for your input.

I've resolved my Thunderbird (115.4.1) issue by (while Thunderbird as down), backing up my "new" .thunderbird directory and then replacing it in its entirety with the backup apparently taken during my UbuntuStudio 22.04 installation named "dotfiles_backup_2023-11-12_11-35-04" (only the .thunderbird portion).  I then appended that new "Inbox"  (from that new backup having newly downloaded email), to my older "Inbox" now restored to my .thunderbird directory structure using "[FONT=monospace][COLOR=#000000]cat ~/Documents/Temp/pop.cox.net.2311231235/Inbox >> Inbox" [/COLOR][/FONT](while in the "[FONT=monospace][COLOR=#000000]~/.thunderbird/p5gkks63.default-release/Mail/pop.cox.net[/COLOR]" [/FONT]folder.

However, I had done a significant amount of pre-upgrade research and had never read anything relating to the US2204 installation process backing up and recreating my /home directory "." files (hidden).  I consider this a significant oversight in such installation documentation.  It's possible that I missed it out of my pure ignorance, but if so, being a Sr. Systems Programmer in the mainframe arena for decades, I've gotta believe a huge number of Ubuntu users will also "miss" it.  I believe a close examination of the installation package addressing that issue would benefit a significant number of users.

I still have the balance or my hidden directory structure to deal with, but will probably wind up restoring most, if not all, of it to it's original path before reinstalling related packages.

Thank you again for your time and input.  I hope sharing my experience will benefit others surprised by this behavior, or otherwise simply dealing with merging of Thunderbird mailboxes.

---

### Post by ajgreeny on 2023-11-24
Great news!
Please mark as SOLVED from Thread Tools top right of the page.

---


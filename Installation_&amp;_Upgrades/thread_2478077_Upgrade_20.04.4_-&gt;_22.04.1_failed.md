---
title: "Upgrade 20.04.4 -&gt; 22.04.1 failed"
date: 2022-08-16
forum: Installation &amp; Upgrades
---

### Post by tinyfooler on 2022-08-16
Hello,
during the upgrade at some point early in the package installation phase the screen went black and did not return to graphics mode after several minutes. Some error messages appeared on the terminal screen, but I do not remember now, what they said. It were two different messages repeated twice each.
I switched to tty2 and could login there.
The welcome message suggested, that a reboot is required. So I rebooted using sudo reboot, hoping that the installation would resume.
However it didn&#8216;t. I can login on tty but any attempts to have apt resume the installation fail due to unresolved dependencies (~ 100 of them). Many of them regard python3 and libqt5 related packages.
apt --fix-broken install
shows (after a long list of unresolved dependency messages)
E: Fehler: Unterbrechungen durch pkgProblemResolver::Resolve hervorgerufen: dies könnte durch zurückgehaltene Pakete verursacht worden sein.
E: Abhängigkeiten konnten nicht korrigiert werden.

Has anybody got a recommendation how I can recover this system and complete the upgrade?
Edit: if this helps: The login prompt still reports the system as 20.04.4 LTS

---

### Post by tea for one on 2022-08-16
100 unresolved dependencies does not bode well.
Do you have PPAs in your repository sources?
Please confirm that you have a backup of your personal data?

---

### Post by tinyfooler on 2022-08-16
I have a backup of /home and it is also on a separate partition. There were ppas, but the upgrade process reported to have disabled them.

---

### Post by tinyfooler on 2022-08-16
If I went for a clean install&#8230;
would it be feasible to restore backups of /etc/passwd and /etc/group ? The intention would be to preserve the uids and gids.

---

### Post by tea for one on 2022-08-16
> **tinyfooler said:**
> I have a backup of /home and it is also on a separate partition. There were ppas, but the upgrade process reported to have disabled them.

I would double-check that the PPAs were disabled.
Better still, remove them completely.
Then run:-
```
sudo apt update
```
Post the output in code tags** #**

---

### Post by tinyfooler on 2022-08-16
Hello tea for one,
thanks for the prompt response and willingness to help. I have decided in favour of a fresh setup, given the chances that I might get rid of applications I have already forgotten.
I was confined to the command line and information exchange thus quite difficult (or I&#8216;d have to retype everything here).
Best regards, tinyfooler

---

### Post by tea for one on 2022-08-16
> **tinyfooler said:**
>  I have decided in favour of a fresh setup, given the chances that I might get rid of applications I have already forgotten.

Yes, good choice.
Every two years, when the LTS arrives, I always install from scratch and restore my personal files.
A couple of hours is time well spent and avoids potential grief with in-situ upgrades.

If you agree, you could mark the thread as solved to show other users that a fresh install is often the most effective way to move from one LTS version to the subsequent LTS.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by deadflowr on 2022-08-16
As far as PPAs and 3rd party repositories go, the upgrader only disables the sources for those.

You must determine if those require you to downgrade the ppa packages before the upgrade or not.
Some, like the oibaf graphics driver ppa, state you should run ppa-purge the ppa first before running any upgrades.

You should consult the PPA or 3rd party repository first in order to find if it needs the packages ppa-purged or not.
(And I do not know if ppa-purge will even work for non-ppa 3rd party repositories. I've never needed nor tried it myself)

Without doing so you risk upgrade failures, simply because you probably have packages even newer the upgraded release.
Which can cause oddball dependency issues.

(Note the difference between PPAs and 3rd party repositories in general are PPA are also 3rd party repositories, but are exclusively from launchpad.net.
Where as other non-ppa 3rd party repositories are from anywhere else; it's a fingers and thumbs kind of thing,
all thumbs are fingers but not all fingers are thumbs)


All this is moot, (both above and below, since you've already reinstalled a clean installation, from what I understand)

but as far as the failure goes, the upgrader logs its actions in the /var/log/dist-upgrade folder.
Usually in a few logs like apt.log, apt-term.log, main.log, and history.log.
Those can usually give you some idea of what went wrong.

Not that any of this is helpful for what happened, but maybe it can be for the future.

---

### Post by SeijiSensei on 2022-08-16
You need /etc/shadow, too. That's where the encrypted passwords are stored

I maintain a directory on my server with the passwd, group, and shadow authentication files, along with address books for Thunderbird, bookmarks and passwords for Firefox, and some useful files like additions to /etc/hosts for machines on my private network and the NFS entries that I need to add to /etc/fstab. Makes a new installation go much faster.

---

### Post by tinyfooler on 2022-08-16
Thanks SeijiSensei for the hint with /etc/shadow. I will retrieve that from my backup as well. Incidentally I found that replacing the entire /etc/passwd with the backup is not such a good idea. Probably other uids for service accounts have also changed after a new install. So I selectively edited the uids for the user accounts.
I remembered to save my fstab, thank you. ;-)

---

### Post by tinyfooler on 2022-08-16
> **deadflowr said:**
> 

but as far as the failure goes, the upgrader logs its actions in the /var/log/dist-upgrade folder.
Usually in a few logs like apt.log, apt-term.log, main.log, and history.log.
Those can usually give you some idea of what went wrong.

Not that any of this is helpful for what happened, but maybe it can be for the future.

Indeed, I think this is valuable information for other people finding this thread. Thank you.

---

### Post by tinyfooler on 2022-08-16
> **tea for one said:**
> Yes, good choice.
Every two years, when the LTS arrives, I always install from scratch and restore my personal files.
A couple of hours is time well spent and avoids potential grief with in-situ upgrades.

If you agree, you could mark the thread as solved to show other users that a fresh install is often the most effective way to move from one LTS version to the subsequent LTS.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Well, My system was originally set up with 16.04, taking all LTS dist-upgrades ever since. So far that went well. But I would assume that deadflowr&#8217;s remarks probably have got s.th. to do with the calamity. Thanks to everyone who posted! I appreciate it. Now I go looking for the solved button. This was my first thread.

Edit: And it&#8217;s more likely a couple of weeks until I will be up to speed again. Backup system, Postgres, &#8230; all the tools of my grown infrastructure.

---


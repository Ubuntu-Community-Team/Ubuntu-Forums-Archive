---
title: "Error:no apt upgrade possible...403 forbidden error"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by Rapy on 2007-06-04
Hello, I have a serious problem since 3 days...I cannot use apt because of a 403 forbidden error...I tried to change the conf of sources.list and I tried to update apt but the same error is still there...I think it's a problem of autentication permission of whatever else, but I'm a newbie and I dont know what can be...

here is sources.list
> 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
## deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) edgy universe
## deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
## deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

Result of apt update:
> 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty Release.gpg
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-it
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-it
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/multiverse Translation-it
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Translation-it
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-it
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-it
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/universe Translation-it
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-it
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-updates Release.gpg
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-it
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-it
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-updates/multiverse Translation-it
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-it
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-updates/universe Translation-it
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages
403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty Release
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Sources
403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
403 Forbidden
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/multiverse Packages
403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
403 Forbidden
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/universe Packages
403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
403 Forbidden
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-updates/multiverse Packages
403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
403 Forbidden
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-updates/universe Packages
403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
403 Forbidden
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
403 Forbidden
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
403 Forbidden
Impossibile ottenere [http://wine.budgetdedicated.com/apt/...86/Packages.gz](http://wine.budgetdedicated.com/apt/...86/Packages.gz) 403 Forbidden
Impossibile ottenere [http://wine.budgetdedicated.com/apt/...rce/Sources.gz](http://wine.budgetdedicated.com/apt/...rce/Sources.gz) 403 Forbidden
Impossibile ottenere [http://security.ubuntu.com/ubuntu/di...86/Packages.gz](http://security.ubuntu.com/ubuntu/di...86/Packages.gz) 403 Forbidden
Impossibile ottenere [http://security.ubuntu.com/ubuntu/di...86/Packages.gz](http://security.ubuntu.com/ubuntu/di...86/Packages.gz) 403 Forbidden
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) 403 Forbidden
Impossibile ottenere [http://security.ubuntu.com/ubuntu/di...rce/Sources.gz](http://security.ubuntu.com/ubuntu/di...rce/Sources.gz) 403 Forbidden
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/...86/Packages.gz](http://it.archive.ubuntu.com/ubuntu/...86/Packages.gz) 403 Forbidden
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) 403 Forbidden
Impossibile ottenere [http://security.ubuntu.com/ubuntu/di...rce/Sources.gz](http://security.ubuntu.com/ubuntu/di...rce/Sources.gz) 403 Forbidden
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/...86/Packages.gz](http://it.archive.ubuntu.com/ubuntu/...86/Packages.gz) 403 Forbidden
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz](http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz) 403 Forbidden
Impossibile ottenere [http://security.ubuntu.com/ubuntu/di...86/Packages.gz](http://security.ubuntu.com/ubuntu/di...86/Packages.gz) 403 Forbidden
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/...86/Packages.gz](http://it.archive.ubuntu.com/ubuntu/...86/Packages.gz) 403 Forbidden
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz](http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz) 403 Forbidden
Impossibile ottenere [http://security.ubuntu.com/ubuntu/di...86/Packages.gz](http://security.ubuntu.com/ubuntu/di...86/Packages.gz) 403 Forbidden
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/...86/Packages.gz](http://it.archive.ubuntu.com/ubuntu/...86/Packages.gz) 403 Forbidden
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) 403 Forbidden
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) 403 Forbidden
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz](http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz) 403 Forbidden
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz](http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz) 403 Forbidden
Lettura della lista dei pacchetti in corso... Fatto
E: Impossibile scaricare alcune file di indice, essi verranno ignorati, oppure si useranno quelli precedenti.

---

### Post by mys_shekar on 2007-06-04
Are you able to ping them separetly??  Are you using a proxy firewall? If yes then make sure u use the proxy command and try.

---

### Post by IllegalCharacter on 2007-11-16
I'm getting this same problem, was there a solution for this?

---

### Post by jdong on 2007-11-16
A bug was identified in the update associated with USN-544-1 [http://www.ubuntu.com/usn/usn-544-1](http://www.ubuntu.com/usn/usn-544-1)

As a result, the update was disabled to prevent users from inadvertently upgrading to this defective release.

When the problem is resolved, the permissions will be restored to normal. Thanks for everyone's patience and understanding.

---

### Post by jdong on 2007-11-16
Sticking this thread for 24hr

---

### Post by tonyhawz on 2007-11-16
I did manage to upgrade that samba package :?
I hope that no one want to DDOS attack me

---

### Post by saultpastor on 2007-11-16
What was the bug?

Maybe has nothing to do with it but I had some updates that had accumulated over the past few days and I updated just before lunch.  I then rebooted to try out a live CD (Mythbuntu) played with it for a bit then rebooted. 

It couldn't find my nvidia drivers, I reinstalled them using envy, restarted, and everything seems fine right now. 

Could this have been related?

---

### Post by jdong on 2007-11-16
No, the bug was related to nmbd crashing on Dapper and Edgy on a specific Samba setup. For all supported releases, the update failed to patch a security problem in smbfs, so all of the updates are pulled as they are reworked across the board.

Ubuntu isn't the only distro to be afflicted by this problem -- Redhat and others were plagued by similar update problems.

---

### Post by neonkat on 2007-11-16
So the instruction is to wait until this is fixed then try again? Please correct me if I'm wrong in this assumption.

Thanks for your assistance and time.

Neonkat.

---

### Post by trtech on 2007-11-16
I was in the middle of upgrading to 7.10 when this happened. I'm assuming that it's what crashed the update and left my system unbootable. That sucks. Bad.

---

### Post by tonyhawz on 2007-11-16
> **neonkat said:**
> So the instruction is to wait until this is fixed then try again? Please correct me if I'm wrong in this assumption.

yeah, there is no other option , besides that there is not big deal to have your updates a bit delayed, the only thing is the annoying orange icon next to nm-applet :P

we will have to wait for them to run chmod +r *.deb

---

### Post by Ek0nomik on 2007-11-16
> **neonkat said:**
> So the instruction is to wait until this is fixed then try again? Please correct me if I'm wrong in this assumption.

Thanks for your assistance and time.

Neonkat.

Yes.  The reason you're getting that error is because the files were pulled from the servers you download from because of the bug report.  If you wait until they put the files back on you can update without a hitch.

> **trtech said:**
> I was in the middle of upgrading to 7.10 when this happened. I'm assuming that it's what crashed the update and left my system unbootable. That sucks. Bad.

What happened?  The bug (to my knowledge) doesn't crash your system, it simply makes your system vulnerable to an attack.  Perhaps it is another non-related issue which made your system unbootable?  I found Gutsy to be the most unstable release yet, but that's just me.  :)

```
When samba is configured as a Primary or Backup Domain Controller, a remote attacker could send malicious logon requests and possibly cause a denial of service. (CVE-2007-4572)
```

---

### Post by tonyhawz on 2007-11-16
> **Ek0nomik said:**
> What happened?  The bug (to my knowledge) doesn't crash your system, it simply makes your system vulnerable to an attack.  Perhaps it is another non-related issue which made your system unbootable? ]

samba didn't crashed for him , but the upgrade did.

---

### Post by FuturePilot on 2007-11-16
Uh-oh. I didn't receive this error and I installed the update earlier this morning. On all 3 computers #-o
Should I be ripping the internet out of the wall?

---

### Post by jwmislan on 2007-11-16
I have a bunch of updates along with the Samba packages that were being held up by the 3 Samba packages bug-problem. I need to get on with my work today, so I'm un-selecting Samba packages updates for now. 
( close the error box ) - ( un check any one of the Samba packages in update manager window this will automaticily un-check all 3 ),
\ now continue with update .   

This will allow me to finish updating the other packages.
In my case  there were no dependencies with the 3 Samba packages -

 libsmbclient - samba-common - smbclient 

Done - it was successful. 

Now I'll just ignore the 3 Samba updates in the update manager tray until the issue is resolved .

Back to whatever it was that I was doing before : -

Cheers
John WM

---

### Post by marco.bomben on 2007-11-16
Hi all,
           I'm stuckhere:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.24-2ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.24-2ubuntu1.3_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.24-2ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.24-2ubuntu1.3_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.24-2ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.24-2ubuntu1.3_i386.deb)
  403 Forbidden


This stopped me to update to Gutsy too.

Any help would be great. Thanks!

Marco

---

### Post by tonyhawz on 2007-11-16
> **marco.bomben said:**
> This stopped me to update to Gutsy too.

did it break your system ?
someone has to post something in big fonts , something like DONT UPGRADE TO GUTSY TODAY!!

---

### Post by Ek0nomik on 2007-11-16
> **tonyhawz said:**
> did it break your system ?
someone has to post something in big fonts , something like DONT UPGRADE TO GUTSY TODAY!!

Not fetching those Samba files won't break your system, it simply won't upgrade Samba.

---

### Post by derrill on 2007-11-16
Can someone update this thread once the permission thing is fixed?  
(I'm anxious to use the new samba features...)

---

### Post by arkara on 2007-11-16
ok i just sat on my pc and i had some updates to do.
i got the same msg.. and i cant install my updates.

---

### Post by Happy_Man on 2007-11-16
Whoof, thank god. I thought Verizon had started blocking Ubuntu updates or something. :-s 8-[ :shock:

Plus, I use Samba (regularly, as this comp also serves as the house's media server), so this update could have borked my painstakingly setup config. Yay for Ubuntu! Now, if this was Microsoft, they would have let the update roll out anyway, and then everyone would be bitching about their crashed networks. :p

---

### Post by joao82 on 2007-11-16
I can't update either, but I get only this as error:
"There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages. "

is it related?
I had the same two days ago with an update to the qt_plugins_3.3rc configuration file. And i lost connection during an update download at the same time. Now I'm afraid my update manager is all messed up.

---

### Post by d_demchuk on 2007-11-16
My update ground to a halt. I tried to cancel but there wasn't really any way to do that, so I tried to close the update window...no success. I bravely/foolishly rebooted and found that I could go all the way to entering my username and password, but then ended up at a blank screen (in the customary Ubuntu creamy orange) with a mouse arrow. And that was it. 

Any suggestions on what I should do next?

David in Toronto

---

### Post by gaspard.leon on 2007-11-16
I get this when trying to install updates (17 Nov 2007)

[INDENT]
[FONT="Courier New"]W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden[/FONT]


[/INDENT]

---

### Post by asbjornu on 2007-11-16
I get this error now too. Would be nice if someone could alter the permission on these samba files so people can upgrade properly. Or, if it's a security risk to update, remove these files as available upgrades at least until the security hole is patched! :)

---

### Post by TiMBuS on 2007-11-16
> **jdong said:**
> A bug was identified in the update associated with USN-544-1 [http://www.ubuntu.com/usn/usn-544-1](http://www.ubuntu.com/usn/usn-544-1)

As a result, the update was disabled to prevent users from inadvertently upgrading to this defective release.

When the problem is resolved, the permissions will be restored to normal. Thanks for everyone's patience and understanding.

Huh?
The bug says:
```
The problem can be corrected by upgrading your system to the following package versions:
..
Ubuntu 7.10: 
samba 3.0.26a-1ubuntu2.1
```

Now from what I see, the listed update in the update manager is indeed, samba 3.0.26a-1ubuntu2.1.
Am I missing something here? It seems you are preventing me from being allowed to patch my samba flaw. =/

---

### Post by jdong on 2007-11-16
No no, the bug is in the **updated package** referred to by the USN. The update itself is flawed, which is why it is currently blocked from downloading. It incompletely fixes the vulnerability and even crashes on some systems.

---

### Post by TiMBuS on 2007-11-16
Ah, that makes more sense now.
Thanks for explaining that.

---

### Post by d_demchuk on 2007-11-16
So...any ideas on how I get back to the version of Gutsy I had before my update crash? I tried booting previous versions--including recovery versions--at bootup with no success, i.e. low res graphics, an X cursor and no further progress than before.

David in Toronto

> **d_demchuk said:**
> My update ground to a halt. I tried to cancel but there wasn't really any way to do that, so I tried to close the update window...no success. I bravely/foolishly rebooted and found that I could go all the way to entering my username and password, but then ended up at a blank screen (in the customary Ubuntu creamy orange) with a mouse arrow. And that was it. 

Any suggestions on what I should do next?

David in Toronto

---

### Post by persephone977 on 2007-11-16
Thanks for the info--this just showed up for me today. Apparently I had to get through all the other updates in sections before I hit this one. Thanks again!

---

### Post by angryfirelord on 2007-11-16
[this part taken out because of brain fart]

Actually, this little experience shows that I have more faith in Ubuntu's security response team.

---

### Post by jdong on 2007-11-16
> **angryfirelord said:**
> In the meantime, choose a different server as the others probably haven't synced up to the flawed update. That way, you won't be getting 403 errors and crashing updates. :)

The only supported action users should take right now is to wait or periodically refresh APT until the 403 disappears. It is not recommended to switch the security source to something other than security.ubuntu.com, or try to force various versions to install, or disable the security repositories. Don't create more trouble for yourself!

> 

Actually, this little experience shows that I have more faith in Ubuntu's security response team.
As I've been told, the actual problem with the update only happens on various (non-default) configs of Samba but they are playing it safe and re-doing the update correctly. It's not something that I'd expect any reasonable time frame QA process to have caught.

---

### Post by Butthead on 2007-11-16
Are you guys ever going to fix the vmware-player upgrade causing adept package manager to lock up bug in Kubuntu 6.06 while you're at it?

---

### Post by praveenpious on 2007-11-16
Thanks for the info, i was beginning to panic :)

---

### Post by killmoon on 2007-11-16
Still no ETA?

---

### Post by sirlancelot on 2007-11-16
I'm beginning to see a trend with Gutsy.... daily package updates! :)

---

### Post by keyboardashtray on 2007-11-16
Glad I found this sticky, heh, was about to go on a wee little rant about adept bugging out again (been the major headache in my otherwise recent decent Ubuntu>Kubuntu switch).

Just out of curiosity, if there is a bad update like this, why isn't the update just yanked off the servers as if there isn't an update to make, instead of keeping it up but locking people out (and causing the confusion)?

I'm sure there is a good technical reason I'm just curious what it is.

---

### Post by FuturePilot on 2007-11-16
So what should I do if I already have installed samba 3.0.26a-1ubuntu2.1:-s
Must have got in before they blocked it.:shock:

---

### Post by angryfirelord on 2007-11-16
> **jdong said:**
> The only supported action users should take right now is to wait or periodically refresh APT until the 403 disappears. It is not recommended to switch the security source to something other than security.ubuntu.com, or try to force various versions to install, or disable the security repositories. Don't create more trouble for yourself!
:oops: Guess I should've read this a little more.

---

### Post by ThrobbingBrain66 on 2007-11-16
> **Butthead said:**
> Are you guys ever going to fix the vmware-player upgrade causing adept package manager to lock up bug in Kubuntu 6.06 while you're at it?

Have you reported the bug on Launchpad yet?  If it's already been reported, maybe you should add you two-cents there.  Maybe the bug has been forgotten about.  This thread has nothing to do with your complaint.

One thing can be certain.  If they had a solution for the bug, it would've been released by now.

---

### Post by navneeth on 2007-11-16
Ubuntu does not start after I installed a bunch of updates. Someone please help me. 

[http://ubuntuforums.org/showthread.php?t=614731](http://ubuntuforums.org/showthread.php?t=614731)

---

### Post by jdong on 2007-11-16
> **FuturePilot said:**
> So what should I do if I already have installed samba 3.0.26a-1ubuntu2.1:-s
Must have got in before they blocked it.:shock:

As long as Samba isn't crashing on startup, you are fine (it should not on most setups) -- if so, you'll be without Samba until this bug is resolved.

---

### Post by FuturePilot on 2007-11-16
> **jdong said:**
> As long as Samba isn't crashing on startup, you are fine (it should not on most setups) -- if so, you'll be without Samba until this bug is resolved.

Ok, thanks :)

---

### Post by Tris2006 on 2007-11-16
I hope the problem gets resolved soon. I was looking forward to getting Gusty back on my laptop. I only got my hands on a 7.04 disk. So I guess im stuck with Feisty for a while. Ah well. No big deal. Ubuntu is Ubuntu all the same. :)

---

### Post by jdong on 2007-11-17
Please be patient -- the update will be re-released in reasonable time. The worst thing the Security team could do right now is be hasty under pressure and release another set of defective updates. Please back off and let the process run its course -- we are working on it :)

---

### Post by navneeth on 2007-11-17
> **jdong said:**
> Please be patient -- the update will be re-released in reasonable time. The worst thing the Security team could do right now is be hasty under pressure and release another set of defective updates. Please back off and let the process run its course -- we are working on it :)
What's the solution to someone who cannot access Ubuntu gutsy at all?

---

### Post by jdong on 2007-11-17
> **navneeth said:**
> What's the solution to someone who cannot access Ubuntu gutsy at all?

I'm not sure if your problem is related to this Samba update in any way.

---

### Post by d_demchuk on 2007-11-17
I'm having the same problem as Navneeth. I have Samba and had not updated it (as far as I know) prior to this release--but it seemed that my update ground to a halt while unpacking one of the lib... files. I tried to stop the update manager, then when I couldn't I rebooted--and found I couldn't get into Gutsy at all.

Do I need to reinstall?

---

### Post by praveenpious on 2007-11-17
> **keyboardashtray said:**
> Just out of curiosity, if there is a bad update like this, why isn't the update just yanked off the servers as if there isn't an update to make, instead of keeping it up but locking people out (and causing the confusion)?
I'm sure there is a good technical reason I'm just curious what it is.
I have to agree with that, The bad update is still being listed for me.

---

### Post by AJB2K3 on 2007-11-17
As so this explains the
smbclient updage errors im getting

---

### Post by joao82 on 2007-11-17
It's working now!
updating samba :D


at least, I hope these are the new packages... 


```
joao@portatil:~$ sudo apt-get update
[...]
Get:3 http://security.ubuntu.com gutsy-security Release [51.2kB]
[...]
joao@portatil:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  libsmbclient samba-common smbclient
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 8606kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://security.ubuntu.com gutsy-security/main smbclient 3.0.26a-1ubuntu2.2 [4886kB]
2% [1 smbclient 189897/4886kB 3%]

```

---

### Post by ghowells on 2007-11-17
Excellent, I think we all owe a sincere thank you to Jdong for keeping us in the loop.

---

### Post by gonsolo on 2007-11-17
Hi!

I had to manually update the sources. Otherwise the automatic software installation tries to download the old samba again. I think it would be better for future mistakes if this program updates itself before trying to download new packages.

g

---

### Post by God_Bless on 2007-11-17
> **praveenpious said:**
> I have to agree with that, The bad update is still being listed for me.

You have to remember that it isn't microsoft. They aren't making billions of dollars and paying a bunch of people to work on bugs. If they mess with yanking that update off the server the longer it will take to replace the the bad string with a good one. They will just wait until they have a good string and do it all at once.

---

### Post by kamikazi on 2007-11-17
I think this problem had solved. I was able to upgrade to 7.10 and it seems like work very well.
But after i finish the upgrade, my Firefox just stop woking and it got some problem with the extention like i couldnt sign in to my del.icio.us bookmark. Anyone got a solution for this?

---

### Post by tiddlygoose on 2007-11-17
Welp, It seems to be fine now and I had tried the Auto version around 2AM and no go. Now it works so it must be good to go...\\:D/

---

### Post by jdong on 2007-11-17
Yep, the problem is resolved now. Let's give a big round of applause to the Security team and archive managers for quickly identifying the problem, preventing it from spreading, and fixing it all within a day's time :)

---

### Post by taurus on 2007-11-17
> **jdong said:**
> Yep, the problem is resolved now. Let's give a big round of applause to the Security team and archive managers for quickly identifying the problem, preventing it from spreading, and fixing it all within a day's time :)

=D> =D> =D>

---

### Post by mike.123850 on 2007-11-17
As of 9:47 PST, using the Update Manager for 7.10 I am still getting these error messages:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


Mike

---

### Post by AJB2K3 on 2007-11-17
Click **check **to update the list !
That caught me out .

---

### Post by holomorph on 2007-11-17
I was getting that as well w/ the update manager.  

I tried:
```
sudo apt-get update
sudo apt-get upgrade
```
on the command line and that fixed it.

---

### Post by Cariboo1938 on 2007-11-17
I got an automatic Update Notification and when I stared the procedure the
Update Manager reported this:

> An error occurred
The following details are provided:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.24-2ubuntu1.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.24-2ubuntu1.3_amd64.deb)
  403 Forbidden

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.24-2ubuntu1.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.24-2ubuntu1.3_amd64.deb)
  403 Forbidden

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.24-2ubuntu1.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.24-2ubuntu1.3_amd64.deb)
  403 Forbidden

Date: Saturday Nov. 17, 07 10:00 Pacific Time:confused:


[COLOR="Lime"]EDIT: Update completed. System up to date.
           Sunday Nov. 18, 07  10:10 Pacific Time[/COLOR]

---

### Post by mike.123850 on 2007-11-17
> **AJB2K3 said:**
> Click **check **to update the list !
That caught me out .

Clicking on "Check" first, then "Install" did the trick. Thanks for the heads up!

Mike

---

### Post by sirlancelot on 2007-11-17
> **jdong said:**
> Yep, the problem is resolved now. Let's give a big round of applause to the Security team and archive managers for quickly identifying the problem, preventing it from spreading, and fixing it all within a day's time :)

\\:D/ Yay! Well done everyone.

---

### Post by quickshade on 2007-11-17
I'm no security master or programming guru but it seems that adding something to the server that tells you these updates aren't available right now and it would also tell the update manager to ignore them for 12 hours and then refresh the update manager after those 12 hours to look for new packages. Seems like that would be the best way to handle this issue. The ubuntu security team did what was right by pulling the packages but we need something that makes sure people understand thats what is going on, Not something saying they can't access these updates.

---

### Post by jdong on 2007-11-17
> **quickshade said:**
> I'm no security master or programming guru but it seems that adding something to the server that tells you these updates aren't available right now and it would also tell the update manager to ignore them for 12 hours and then refresh the update manager after those 12 hours to look for new packages. Seems like that would be the best way to handle this issue. The ubuntu security team did what was right by pulling the packages but we need something that makes sure people understand thats what is going on, Not something saying they can't access these updates.


Matt Zimmerman (Tech Board) acknowledged this way of handling faulty updates is utterly confusing to users and stated on the ubuntu-devel-discuss mailing list that they are working on better ways of handling these situations.

---

### Post by pswartout on 2007-11-17
Can i just say

a) well done to whoever maintains and looks after the software repository. Stopping us simpletons (AKA end users) from screwing up our systems is very commendable

b) it never ceases to amaze me how much support is available for something that is by all accounts free to the majority

Well done! :-)

---

### Post by pswartout on 2007-11-17
At least it's better than some vendors who ship a product with security holes, release service packs (I think Microsoft still release service packs ... whoops there goes my attempt at vendor neutrality) with even more holes over and over again whilst the end user is blissfully unaware.
I do agree that some sort of control should be engineered into the update process which gives what I believe the trade calls "user friendly feedback" but following the KISS method, stopping people getting files is quick, simple and effective if that's all that's available.
That said I would assume that there are many many software engineers out there who could come up with something ..

---

### Post by george3095 on 2007-11-17
I just need clarification if all these people are having the same problem as I and for the same reason(s): the updates I could not make were for "libsmbclient, samba, samba-common, and smbclient". Do we all have the same problem?

---

### Post by rwmacleod on 2007-11-17
Yes, that's the same upgrade list that everyone was stuck at.

Now, if you click on the "Check" button in Update Manager, you should be able to do the install. Mine just downloaded and is installing now.

// Randy

---

### Post by jon_williams on 2007-11-17
I wasn't sure what was going on when I upgraded two of my machines last night - one seemed to go OK, the other got the 403 error ....
Fortunately, I looked up this thread and having been following the progress. Just done the Check and Install thing - everything seems back in order, phew  :-D

[IMG]http://serve.dynasig.net/4087.gif[/IMG]

---

### Post by mcmunt on 2007-11-17
Nice work to all those involved.

I struck the problem on a Gutsy patch update and a Edgy->Feisty server upgrade at the same time. No problems, just waited and now we're all done.

Cheers
[Mike]("http://www.wekadesign.co.nz")

---

### Post by Butthead on 2007-11-17
> **ThrobbingBrain66 said:**
> Have you reported the bug on Launchpad yet?  If it's already been reported, maybe you should add you two-cents there.  Maybe the bug has been forgotten about.  This thread has nothing to do with your complaint.

One thing can be certain.  If they had a solution for the bug, it would've been released by now.

It's been reported on at least twenty webpages I know of and probably Launchpad. 

Maybe someone has come up with a "fix" for it already (I don't really know?).  But if there is a fix for it, don't you think the Ubuntu crew should let people know (for those who don't have the time to constantly scan webpages trying to get stuff fixed)?

---

### Post by kink1024 on 2007-11-17
I was having the same issue but stumbled on just installing libsmbclient first then the samba packages installed without error.

---

### Post by tonyhawz on 2007-11-18
today a box where I have the flawed package installed upgraded that smb package again.
So I think that mean that the problem is solved .

---

### Post by Cariboo1938 on 2007-11-18
Thanks to whom it may concern...:)
Update completed. System up to date.
Sunday Nov. 18, 07 10:10 Pacific Time
__________________

---

### Post by quickshade on 2007-11-20
> **jdong said:**
> Matt Zimmerman (Tech Board) acknowledged this way of handling faulty updates is utterly confusing to users and stated on the ubuntu-devel-discuss mailing list that they are working on better ways of handling these situations.
Thats good news. Again it doesn't have to be anything fancy, just nice and easy. I'm just glad they realize it's a problem and aren't sitting around like some companies....windows.

---

### Post by Ituxlinux on 2007-11-20
Still having problems upgrading to 7.10 (Nov 20 2007, 1:08 am)

Here is a short list of errors I got:
```

New distribution release '7.10' is available  [Upgrade]
===========================================================================================================

Distribution Upgrade
Upgrading Ubuntu to version 7.10
Preraring the Upgrade
.
.
.

==========================================================================================================
Error during update
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg Could not resolve 'archive.ubuntustudio.org'
Failed to fetch http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2 Could not resolve 'archive.ubuntustudio.org'
Failed to fetch http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz Could not resolve 'archive.ubuntustudio.org'
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://home.eng.iastate.edu/~superm1/dists/feisty/all/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://www.in.fh-merseburg.de/~jahn/opensync-0.21/dists/feisty/main/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://home.eng.iastate.edu/~superm1/dists/feisty/all/source/Sources.gz 404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/source/Sources.gz Could not resolve 'archive.ubuntustudio.org'
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz 404 Not Found
Failed to fetch http://www.in.fh-merseburg.de/~jahn/opensync-0.21/dists/feisty/main/source/Sources.gz 404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz 404 Not Found

[x Close]

```

I don't know if this is important, I don't need to upgrade just now, but what the hell is this?

If I try to partially upgrade
```

Not all updates can be installed
Run a partial upgrade, to install as many updates as posible

This can be caused by:
A previous upgrade which didn't complete
Unofficial software packages not provided by Ubuntu
Normal changes of a pre-release version of Ubuntu

**[Patial Upgrade]**  [x Close]

==========================================================================================
Running Partial Upgrade
==========================================================================================
Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.
audacity
compiz
compiz-core
compiz-gnome
compiz-plugins
gaim
gstreamer0.10-plugins-bad
libfuse2
libpt-1.10.10-plugins-alsa
libtotem-plparser7
mozilla-thunderbird
pidgin
pidgin-data
rhythmbox
thunderbird
totem
totem-gstreamer

[x Close]

```


Any Ideas??

Thanks

---

### Post by jdong on 2007-11-20
Please edit your /etc/apt/sources.list file and remove all entries from non-official repositories. You may add them back later after the upgrade.

---

### Post by tonyhawz on 2007-11-22
> **Ituxlinux said:**
> Still having problems upgrading to 7.10 (Nov 20 2007, 1:08 am)

you may also want to run 
```
sudo apt-get update
sudo apt-get upgrade
```

after removing the non-official repos and before upgrading to 7.10

I hope it helps

---

### Post by tonys_ub on 2007-11-22
When I go into system up-to-date i get a window that pops up and says: "not all up date can be installed" and it says "partial upgrade". So i hit partial upgrade, then i get a distribution upgrade window, it runs for a second, then i get "error authenticating some packages". What should i do?

---

### Post by tonyhawz on 2007-11-23
did you run apt-get update ?

---


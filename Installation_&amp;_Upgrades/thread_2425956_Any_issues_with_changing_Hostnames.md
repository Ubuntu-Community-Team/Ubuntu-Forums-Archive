---
title: "Any issues with changing Hostnames?"
date: 2019-09-02
forum: Installation &amp; Upgrades
---

### Post by anthonyl2019 on 2019-09-02
New to Linux.

My initial setup of Kubuntu 18.04 LTS offered a default hostname of username+machine, namely: 

al-HP-EliteBook-8440p

I've since had various attempts at setting SAMBA up to allow Windows access.  testparm reported a too long Netbios name and in the various attempts to get access I tried to shorten the Netbios name to simply hplinux and furthermore I then altered the Hosts file and Hostname files to hplinux

The workgroup I was trying to join is called Datarevue (this is just a Windows workgroup on my local lan).

Thus  Hosts has entries:
```

127.0.0.1 localhost
#127.0.1.1 al-HP-EliteBook-8440p.Datarevue
127.0.1.1 hplinux.Datarevue

```

Hostname has:
hplinux

and my smb.conf contains: netbios name = hplinux

However I notice that pdbedit -L -v has inconsistencies in my main username, which remains at:
AL-HP-ELITEBOOK-8440P

```

Unix username:        al
NT username:          
Account Flags:        [U          ]
User SID:             S-1-5-21-3873971109-3693196326-484772653-1001
Primary Group SID:    S-1-5-21-3873971109-3693196326-484772653-513
Full Name:            al
Home Directory:       \\hplinux\al
HomeDir Drive:        
Logon Script:         
Profile Path:         \\hplinux\al\profile
Domain:               AL-HP-ELITEBOOK-8440P

```

Although I have SAMBA in an operational state (though not working exactly as desired) I would like to clean up and thus want to know:

1) Are there any issues with having a Netbios name differing from the Hostname, so could I put my hostname back to AL-HP-ELITEBOOK-8440P and leave the netbios name at the shortened hplinux?
2) Would the approach to delete the Samba user al and then recreate be correct once the Hosts/Hostname/Netbios are all sorted
3) Would problems be expected with the current settings?

Any other observations?

---

### Post by TheFu on 2019-09-02
**any** issues?  Sure.  Sometimes IP is used and DNS is used, not broadcasts to find systems on the network.  Avahi takes the hostname.local mode to broadcast for zeroconf systems commonly used by media players.

Also, I would never allow mixed case in hostnames (or groups or usernames).  Always go lowercase.  Yes, it shouldn't matter, but if just 1 script written by 1 guy half a world away doesn't convert them all to lowercase before performing comparisons, BAM, that script won't work.

Having the samba hostname and Unix hostname and Unix DNS name match is also about my sanity.

---

### Post by Morbius1 on 2019-09-02
You've made this way more complicated that it needed to be for 3 lan-networked systems. Anyhoo ...

> 1) Are there any issues with having a Netbios name differing from the  Hostname
No.
> , so could I put my hostname back to AL-HP-ELITEBOOK-8440P and  leave the netbios name at the shortened hplinux?
I wouldn't do it.
> 2) Would the approach to delete the Samba user al and then recreate be correct once the Hosts/Hostname/Netbios are all sorted
If you are talking about this crazy thing: [highlight] Domain:               AL-HP-ELITEBOOK-8440P [/highlight], yes. Just do a:
```
sudo smbpasswd -x al
```
Followed by a
```
 sudo smbpasswd -a al
```

---

### Post by SeijiSensei on 2019-09-02
Use "sudo hostnamectl --set-hostname hplinux" to make the Linux hostname correspond to the netbios name.

See "[man hostnamectl]("http://man7.org/linux/man-pages/man1/hostnamectl.1.html")" for details.

---

### Post by TheFu on 2019-09-02
> **SeijiSensei said:**
> Use "sudo hostnamectl --set-hostname hplinux" to make the Linux hostname correspond to the netbios name.

See "[man hostnamectl]("http://man7.org/linux/man-pages/man1/hostnamectl.1.html")" for details.

Does that modify the /etc/hosts file and /etc/hostname too? The manpage says it does one, but nothing about the other. Then there are network services which might be configured to use a specific hostname, like the MTA uses /etc/mailhost and 
mailname

All these new fangled commands that may or may not do all that is needed are hard to follow.

Doubtful this poster is using those, but we don't know.

---

### Post by anthonyl2019 on 2019-09-02
> **TheFu said:**
> Does that modify the /etc/hosts file and /etc/hostname too? The manpage says it does one, but nothing about the other. Then there are network services which might be configured to use a specific hostname, like the MTA uses /etc/mailhost and 
mailname

All these new fangled commands that may or may not do all that is needed are hard to follow.

Doubtful this poster is using those, but we don't know.

I'm at the early stages of setting up.  I merely want to be rid of my Windows computer and the first stage was to establish file sharing so I can softly start working on my many files (office docs, spreadsheets, photos, videos) step by step as I discover which software suits.

The ultimate goal is to to have my Office Outlook->(old windows ce) smartphone sync replaced by Evolution<->Android but I'm not holding my breath.
Had I realised it was going to be so difficult I would have bought a 2nd hand mainframe and dug out my Algol manuals from 1967 :icon_frown:

---

### Post by anthonyl2019 on 2019-09-02
> **Morbius1 said:**
> You've made this way more complicated that it needed to be for 3 lan-networked systems. Anyhoo ...

If you are talking about this crazy thing: [highlight] Domain:               AL-HP-ELITEBOOK-8440P [/highlight]

The install process offered me that name ie username + machine make + model.  If it is a crazy thing then maybe someone should look at the installation routines as I'm not to know better and it wasn't till I got a "too long" Netbios warning (15character?) that I had any concerns.  

I'll attempt modifying things when I'm in a better frame of mind.

---

### Post by TheFu on 2019-09-02
Nobody here works for Canonical. Everyone, including the moderators, are volunteers.

We all come from different backgrounds, with different experiences, so we each of slightly different views on what is and isn't an issue.  There are also many ways to configure sharing for Windows clients.

I don't think Windows Workgroups work anywhere except in Samba settings.  The /etc/hosts file is pure IP networking, not netbios or any other sort.

---

### Post by anthonyl2019 on 2019-09-03
I'm aware of the structure of forums, though in some places I frequent the forums are occasionally visited by their parents.  As a very much newbie to Linux but not computers and desperate to leave Windows behind I'm afraid that on virtually every Linux forum I've been on the quality and care in answers is not aimed at the likes of me and I reacted to a comment about "crazy thing" which was not of my witting volition.  

I am now battling to understand whether all Linux shares go through SAMBA, as indeed some posts imply, or only, as I had originally believed, Windows shares.  I can of course experiment but on one occasion on a different topic such ill-informed actions caused me to lose my Python setup (I didn't know what Python was at the time!!).

---

### Post by Morbius1 on 2019-09-03
You misunderstood my reference to "crazy thing".

This is what you wrote:

> However I notice that pdbedit -L -v has inconsistencies in my main username, which remains at:
AL-HP-ELITEBOOK-8440P

     
 ```
Unix username:        al
NT username:          
Account Flags:        [U          ]
User SID:             S-1-5-21-3873971109-3693196326-484772653-1001
Primary Group SID:    S-1-5-21-3873971109-3693196326-484772653-513
Full Name:            al
Home Directory:       \\hplinux\al
HomeDir Drive:        
Logon Script:         
Profile Path:         \\hplinux\al\profile
[COLOR=#0000cd]**Domain:               AL-HP-ELITEBOOK-8440P**[/COLOR] 
```

That is referencing your old hostname - the "crazy thing".

That will be resolved to show hplinux if you do a [highlight]sudo smbpasswd -x al[/highlight] then a [highlight]sudo smbpasswd -a al[/highlight]

And yes, the "crazy thing" is the way the Ubuntu installer created the  al-HP-EliteBook-8440p host name in the first place.

---

### Post by TheFu on 2019-09-03
I'll take a shot - warning - lots of opinions follow.

> **anthonyl2019 said:**
> I'm aware of the structure of forums, though in some places I frequent the forums are occasionally visited by their parents.  As a very much newbie to Linux but not computers and desperate to leave Windows behind I'm afraid that on virtually every Linux forum I've been on the quality and care in answers is not aimed at the likes of me and I reacted to a comment about "crazy thing" which was not of my witting volition.  


Complex questions where not all the facts are know are hard to provide answers. In Unix, there are usually 50, if not 500, different ways to accomplish any specific task. Each possible answer has good and bad aspects, often determined by the skill of the local admin and other needs for the system(s).

Simple questions, seldom are.

> **anthonyl2019 said:**
> 
I am now battling to understand whether all Linux shares go through SAMBA, as indeed some posts imply, or only, as I had originally believed, Windows shares.  I can of course experiment but on one occasion on a different topic such ill-informed actions caused me to lose my Python setup (I didn't know what Python was at the time!!).

Unix/Linux supports thousands of protocols, so does Windows. I'd guess about 20 are what we could call call file sharing.  Samba is NOT the native file sharing protocol for Unix, NFS is.  I'd say that SMB/CIFS is generally the preferred file sharing method for Windows clients, on a LAN.  While NFS can be used from Windows, most people use Samba.  

I'm an NFS bigot. I use it for for almost all my LAN sharing, except from the single Windows machine that remains doing 4 tasks.  Everything else is handled by Linux or BSD.

Some network file sharing protocols:
* Samba (standalone, workgroup, AD, DFS)
* NFSv3/V4
* ssh-based sshfs/sftp/scp
* p9fs
* webdav / ftp (I'd avoid these)
* torrents
* u9fs (plan9 networked file system)
* dfs (MSFT distributed FS)
* afs (apple's version)
and there are a number of block-level file replication methods, like ceph, sheepdog, gluster, Swift, DRBD, afs (AndrewFS) and perhaps 10 others.

I use 3 of them commonly.
[LIST=1]
[*]NFS on the LAN for all Unix systems
[*]SMB/CIFS from Windows to Unix on the LAN
[*]sshfs/sftp/scp/rsync on the LAN or over the internet, depends what is convenient.
[/LIST]

Out of all of those, only 1 can use the netbios protocol.  All the others use IP.

The main reasons I prefer NFS is that native file permissions for Unix are fully supported.  Samba doesn't do that.  It used to be that NFS was much faster than Samba, but that can be debated and it is dependent on the underlying hardware and file system selected.  On Linux, Linux file systems are faster.  Foreign file systems, like NTFS or FAT32 or exFAT all seem to have measurably slower performance, probably because we commonly use non-kernel drivers for them.

If you just need to copy files to/from Windows to/from Linux, then the WinSCP program on Windows is a drag-n-drop file manager with support for sftp which can be setup for secure transfers over the internet, provided passwords are never used.

---

### Post by anthonyl2019 on 2019-09-03
I've simplified my hosts, hostname, netbios names to something short and taken out any possible complications so for instance:
> 
127.0.0.1 localhost
#127.0.1.1 al-HP-EliteBook-8440p.Datarevue
127.0.1.1 hplinux.Datarevue

now simply reads
127.0.0.1 localhost

Note that I didn't add the .datarevue (my home LAN workgroup) but one of the processes in trying to setup

Anyhow all working now, gory details at:
[https://ubuntuforums.org/showthread.php?t=2425792](https://ubuntuforums.org/showthread.php?t=2425792)

---


---
title: "How can I tell which architecture I'm running?"
date: 2021-11-13
forum: Installation &amp; Upgrades
---

### Post by Krischu on 2021-11-13
I'm running ubuntu 18.04 LTS on a hoster's VM. 

uname -a
Linux mydomain.org 4.15.0-162-generic #170-Ubuntu SMP Mon Oct 18 11:32:08 UTC 2021 i686 i686 i686 GNU/Linux

cat /etc/lsb.release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.6 LTS"

Since I'm having some problems running/installing snapd :

snap install --classic certbot
error: snap "certbot" is not available on stable but is available to install on the following
       channels:

       edge       snap install --edge certbot

       Please be mindful pre-release channels may include features not completely tested or
       implemented. Get more information with 'snap info certbot'.

Reading about this issue I find that it might be a 32 vs. 64 bit problem. I alwys thought I'm running 64bit.

---

### Post by ubfan1 on 2021-11-13
My 64 bit uname claims x86_64 where you have i686, so probably 32 bit.

---

### Post by MAFoElffen on 2021-11-13
Or to separate it out and see versus the cpu arch...:
```

uname -m
cat /proc/cpuinfo | grep -a1 -m1 -e "clflush size"

```

---

### Post by GhX6GZMB on 2021-11-13
just run lshw in a terminal. One of the first lines will tell you if you're 32- or 64-bit.

---

### Post by MAFoElffen on 2021-11-13
> **ml9104 said:**
> just run lshw in a terminal. One of the first lines will tell you if you're 32- or 64-bit.
Example:
```

sudo lshw | awk ' /width: / {print $2 " " $3; exit;}'

```

---

### Post by Krischu on 2021-11-17
Thanks. Shows I'm running 32bit.

Would it be possible to do an upgrade to 64bits?

---

### Post by KBar on 2021-11-17
```
lscpu | sed --silent '2p'

```

If it shows both 32- and 64-bit, your hardware is capable of running 64-bit. If it only shows 32-bit, you can't upgrade your computer to a 64-bit version. Well, you actually can, but it may and most likely will break your system. In case it doesn't, you won't see any difference anyway.

---

### Post by KBar on 2021-11-17
It's as if you were to try to put helicopter blades on a car. Can you do that? Yes. Will it fly? No, because its engine and all the other parts are still that of a car.

---

### Post by TheFu on 2021-11-17
**lscpu**

But **uname -m works** too.

Lots and lots of ways to get this. 

> Would it be possible to do an upgrade to 64bits?
Possible?  Perhaps.  Nobody does that.
I moved a 32-bit desktop running 16.04 to 64-bit desktop with 20.04 about 14 months ago.  The way I did it was:
Make a backup of everything I didn't want to lose. That was data, personal and system settings, and the list of manually installed packages (apt-mark showmanual).  

Then I wiped everything and performed a fresh, minimal, install of the 64-bit OS I wanted.  Next I started putting all the data back as it was on the prior system, exactly in the locations it was on the old system, with the owner, group, permissions, ACLs, and xattrs that were on the old system. Then I selectively restored system settings - cannot just copy everything, since that will break the new system and likely prevent it from booting. My personal settings were restored when I put my HOME directory back.
Last, I took the list of manually installed packages and fed that into APT and told it to install those.  Each package sees the config files and data from the prior install and would do any upgrades that would normally happen automatically. Some packages don't do any config or data upgrades automatic, so we need to know which those are. Typically, the manual setting changes are only needed for server stuff - like Apache, nginx, mariadb, and webapps.  Desktop programs always seem to handle config updates and data migrations automatically - unless there is a flaw in that process.

It took about 30 minutes to finish all of that and I was running a new 64-bit system with a new OS, with almost all the new, updated programs working fine.  Because I'd skipped 4 yrs, some programs I previously used weren't in 20.04 and were unavailable.  All the major stuff - browsers, email, password managers, editors, IRC chat programs were all working and using my prior data and settings.

One thing that did not just work was my backup tool.  Because I use a client/server backup tool and the new client was python3, it was incompatible with my python3-based backup server software. That took me a few days to figure out, but thankfully, with the tool I use, the most recent backup appears as a mirror of the source, so cp or rsync worked 100% fine.  I used rsync, BTW.  If I needed to get a prior version of the backup set, then I'd have to solve that problem in another way ... probably using a read-only NFS share, but that's me.  Hummm. I really like that NFS idea.  Thanks for the question and making me think through it.  CIFS/Samba cannot be used, since they would lose the ownership, group, ACLs and xattrs.  NFS rocks.

So, the real question comes down to "how good and useful are your backups?"  I know that mine are excellent.

---

### Post by grahammechanical on 2021-11-17
I would like to add a bit of clarification. When 64 bit CPUs were produced they were backwards compatible with the code of the 32 bit CPU. This meant that a 32 bit OS and applications could run on a 64 bit CPU. It does not work the other way around. A 64 bit OS and 64 bit applications cannot run on 32 bit CPU's. The architecture of the 32 bit CPU does not match the code of the 64 bit OS.

My first installation of Ubuntu was a 32 bit version but as I had a 64 bit CPU I was able to later on install a 64 bit version of Ubuntu. It was done by a fresh/new install. I doubt if it is possible to upgrade a 32 bit OS to a 64 bit OS except by a fresh install.

Regards

---

### Post by TheFu on 2021-11-17
> **grahammechanical said:**
> I would like to add a bit of clarification. When 64 bit CPUs were produced they were backwards compatible with the code of the 32 bit CPU.  

That was only for Intel x86-64.  Many 64-bit CPUs didn't have 32-bit versions, so they were never backwards compatible or worse, they provided a software translation layer like QEMU for 32-bit programs to run on newer 64-bit hardware.  For example, DEC made the 64-bit DEC-Alpha CPU and there was never a 32-bit version.  They introduced a new OS - OSF/1 as the replacement for 32-bit "Ultrix" which the prior generation of DEC workstations and servers used.  OSF/1 became DigitalUnix - probably as a marketing decision.  The compiled programs from Ultrix couldn't be copied over to OSF and run. They weren't compatible.
However, I know that 32-bit Solaris programs running on the SPARC platform worked on 64-bit Solaris on UltraSPARC CPUs.  For years, I'd bring a copy of tcsh with me to each new job.  OF course, 32-bit x86 Solaris was not binary compatible.

---

### Post by ActionParsnip on 2021-11-17
What CPU is in the system? Does it have a make and model please?

---

### Post by MAFoElffen on 2021-11-17
In post #3, I posted two commands, that you should have posted the output of... (within Code Tags). I didn't explain the reasoning for those, but it seems I needed to. I'm used to being ignored or over-talked/posted... Just a thing that happens. But there was some logic to those that is reappearing here, and is still not resolved. If the OP had done those then, those questions would already be answered... So maybe that is my fault for not explaining.

The first command was the Command that "TheFU" asked for (again) in  his post, post #9... That uses LSB-Release (the application that creates the LSB_Release file) to report the installed system's architecture.

The second command would have answered what is from your Computer's CPU Info file, that reports what the architecture of what your CPU processor is...

Answering both, of those, by posting the output of both, would have answered to you and others here, what architecture is installed, and what architectures your computer is capable of having installed. From what you already have said,  fragmented in posts, is that you have 32bit installed, but your computer is capable of having a 64bit system OS installed.

TheFu can tell you that he has migrated one of his systems from 32bit to 64bit in less than 20 minutes... Notice I said "Migrated". But here is a twist to that...

Like I said, I am used to being ignored. No matters. That is 'what' I see. Good Luck on your migration to a 64bit OS,  but please keep reading...

BUT: (Follow along...)

What people didn't notice, was that the very first sentence of your first post stated that this machine was a VM... A Virtual Machine. So there are some other considerations. It should be easier to migrate your VM to 64bit, than if it was a single physical machine. It already reports that your VM Host System supports 64it OS'es for it's VM Guests... But it really isn't a traditional VM or VM Host system either...

The [COLOR=#ff0000]challenge[/COLOR] is that this was installed through a "snap" in the Snap Store... which I know nothing about that snap... So it is not a traditional "Virtual Machine"... It is presented as a Snap Application, right? But I do not know that the Snap author has both versions in their Snap application... Good Luck on that. 

Sorry that I don't have the time to research that before I go to work this morning. 

You can recreate it as a traditional guest VM, under a VM Host System... That you should be able to migrate to.

Otherwise, you are stuck within the confines of the Snap Application and  it's Snap Author... When the Snap Application is updated, it will  over-write any changes you make to that specific VM within that Snap Application. That is why, if you find you want to make changes to it, or transform it into something else, that you could and should migrate it to a real VM, where you can keep any changes you transform it to.

---

### Post by ubfan1 on 2021-11-17
I find the following gives me a better list of the packages I installed (fewer than apt-mark showmanual alone) :
```
comm -23 <(apt-mark showmanual | sort -u) <(gzip -dc  /var/log/installer/initial-status.gz | sed -n 's/^Package: //p' | sort  -u)
```

---

### Post by MAFoElffen on 2021-11-17
@ubfan1

That will help him to migrate...

I edited my post #13... Please read the "other" challenges the OP has... There are other factors he also needs to consider. 

This is not a physical machine, nor a traditional VM that he is talking about.

---

### Post by MAFoElffen on 2021-11-17
What would be my recommendations on that?

Most VM's in Snap Applications in the Snap Store are Qemu based VM's that are usually started with a Qemu Script... The good news is that they create a persistent Disk Volume file that works with QEMU/KVM.

If you install KVM, you could import the Disk Volume into KVM and run it within KVM. Then create a new VM Guest to install Ubuntu as 64Bit, and migrate the 32bit VM applications and data to it (as 64bit)...

If you do not know how to do that, or need help with that, I suggest Posting a new thread in the Virtualization Section on "Migrating a Snap VM to KVM".

---

### Post by TheFu on 2021-11-17
Definitely check that the host CPU is x86-64.  If it isn't, you'll need to change VM hosts or find a new VPS service.  I wouldn't think 32-bit hardware would even be an option at a VPS since 2010, but perhaps some of the smaller ones use hardware until it dies?

---


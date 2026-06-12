---
title: "OK, I give up!"
date: 2023-07-12
forum: Installation &amp; Upgrades
---

### Post by mag3lxub on 2023-07-12
Refer to [this thread]("https://ubuntuforums.org/showthread.php?t=2484219").

OK, I give up. I've been looking an "easy" way to use Ununtu Server as a Windows style "domain controller" in order ro replace/retire my existing Windows 2003 server.  Originaly, I had installed Ubuntu Server 22.04 LTS (Jamy Jellyfish). I was then looking for the right piece of software that implemented a Microsoft Style "Active Directory."  I had come upon the software, "[Zentyal]("https://zentyal.com/")," a Linux based software to implement Active Directory via the "Samba" product.

Unfortunately, the current rel. of Zentyal (7.0) will not work on Ubuntu Server 22.04 LTS. Using Zentyal 7.0, I would have to revert to Rel. 20.04 of Ubuntu Server, or wait until Zentyal 8.0 is released for 22.04.  I no longer wish to wait. They keep promissing to release Zentyal 8.0 "Soon" but it never happens. 

Well, I attempted to revert back to Ubuntu Server rel. 20.04.  The main problem being, it doesn't recognize my NIC card. The kernel in that release is 5.4x And my NIC card isn't recovnized in the system kernel until kernel 5.9.  And, without that, I can't get any  updates at all.  I can't even install the programs that will let me install the NIC card and all the other software, even if I migrate it on a flash drive.  They just don't work.  I've tried everything and it just doesn't work.

Thus, I give up.  I went ahead and re-installed Ubuntu Server 22.04.  It recognized the NIC card immediately. It installed everything I had installed previously.   I'll use the standard Server Utilities (DHCP, DNS, NTP etc.).that are native to Server 22.04,  but to implement the domain controller service via native Samba.  AFAIK, Zentyal is just merely a shell that abstracts and facilitates native Samba. It's like using WINE vs Bottles.  It may take me a while to implement, but I think that's a better choice, at this point.  

So much for Zentyal.    Should ver 8.0 finally be released, and I haven't yet fully implemented native Samba, then I'll consider it.  

But, for now, I give up (on Zentyal, that is). 

I'll keep everyone posted.  Thanks.

---

### Post by TheFu on 2023-07-12
If you want an MS-Windows Domain Controller, perhaps paying MSFT for their software is the best answer?

If you want to integrate Unix and Linux systems, then Linux/Unix methods would be the best answer.

If we put lipstick on a duck, it is still a duck. Canonical has been working to make Ubuntu desktop systems integrate with MS-AD since 2019.  I remember seeing the "Add Desktop to AD domain" with the 20.04 install.  It is a bit of an embarrassment for Canonical not to ship an LDAP centralized user manager, IMHO as the default way to deal with users, but that's their choice.

In the 1990s, we all used NIS and it was easy to setup and use. Alas, it had terrible security.  Sun Microsystems created NIS+ which solved the security issues, but they kept the server software only on Solaris, which cut off nearly all F/LOSS shops.  NIS+ clients exist for most platforms - though I don't have any clue about MS-Windows.

Management of LDAP on Linux kinda sucks, unless you have a separate tool just for that.  

Then there are other issues since the separate tool is either some suspicious java or php webapp or perhaps it is a huge system that happens to use LDAP, but was designed for other purposes like email accounts or tracking sales contacts.  I used an email tool for LDAP management, but every upgrade of that other system meant I had to remove the POSIX schema from the LDAP, do the upgrade, then put the POSIX schema back and re-modify the email software to maintain the POSIX schema parts.  Eventually, one of those nasty upgrades failed and it was just too much trouble to use anymore.

I miss NIS from a usability standpoint. user, group, netgroup, and password management was all tied to the OS utilities, so everything worked like we expected.  Perhaps my memory is off and I don't recall the problems today, but I remember being amazed and not disappointed with our NIS setup.  The company had 20 employees when I started and we grew to over 3000 ... all under the NIS management.  It was good.

BTW, if you get a newer release of 20.04, you'll find they have newer kernels. My 20.04 systems are on
```
$ uname -r
5.15.0-76-generic
```
Get the Ubuntu Server 20.04.6 ISO.  Almost always, the newer _point_ releases of Ubuntu versions comes with a newer kernel to be installed.  
[https://ubuntu.com/about/release-cycle#ubuntu-kernel-release-cycle](https://ubuntu.com/about/release-cycle#ubuntu-kernel-release-cycle) appears to show some information for which kernels are provided for each release. Not sure if this is clear.

My 22.04 Mint Desktop (21.1 is the mint version) is running:
```
$ uname -r
5.15.0-76-generic

```
Seems like both are newer than 5.9.x.

BTW, my two main systems both have GUIs that didn't get driver support until 5.10.x kernels, so I'm fairly certain the latest 20.04.6 ISO came with 5.15.x kernels.  I just did a fresh, wipe-everything, install in May on one of the systems.

I don't know anything about Zentayl.  

Redhat used to provide FreeIPA as a centralized user/group management server.  Alas, it never ran well on any Ubuntu (or debian-based distros), but there are ubuntu clients for it.  I think when they moved CentOS to a rolling release, Redhat decided to pull that pile of 20 F/LOSS projects, all tightly integrated into FreeIPA using 50 different languages (it is a mess) in-house and make a commercial (for-sale only) product.  OTOH, once F/LOSS, always F/LOSS, so their may be a fork of the FreeIPA system somewhere.   [https://freeipa.org/](https://freeipa.org/)    The guides seem really old and reference non-supported versions of RHEL.  Not a good sign.  LDAP is really light.  FreeIPA servers seem to need 2GB of RAM and 2 cores, minimal. Not light.  I'm at a loss for how something that should be able to run on a Pentium90 from 1997 can become so bloated.

The common LDAP GUI management tools seem to be open ended for the typical Linux flexibility, but that make for issues to people used to being told how to solve a problem like 5million other people do it.  I found a webpage that lists LDAP management tools - of the 6 projects they list, all but one are discontinued, dead.  KLDAP seems to be taken over by the KDE team.  [https://api.kde.org/kdepim/kldap/html/index.html](https://api.kde.org/kdepim/kldap/html/index.html)  Not much there and *apt search* doesn't find a package.

I had hoped that **Cockpit** [https://cockpit-project.org/](https://cockpit-project.org/), a new server management dashboard project, would include LDAP, but my look for that failed. Perhaps I missed it and they call it something else?  [https://cockpit-project.org/guide/latest/sso](https://cockpit-project.org/guide/latest/sso) is the SSO page. Cockpit is in the Ubuntu Repos. Might be worth a look for you.  [https://cockpit-project.org/running.html#ubuntu](https://cockpit-project.org/running.html#ubuntu) has the install and initial use instructions.  Don't worry about "backports" - that's old information.
```
$ apt search cockpit
```
shows lots of modules/packages for cockpit on Ubuntu. Looks promising. Plus, the SSO uses Kerberos, so that's definitely a security/login thing.  Hummmm. Very interesting.  

[https://www.techrepublic.com/article/install-cockpit-ubuntu-better-server/](https://www.techrepublic.com/article/install-cockpit-ubuntu-better-server/) makes Cockpit setup look really easy. I suspect that's not for the Kerberos SSO stuff we all want.

Every year or so, I want to get all my ducks flocking together and using SSO/LDAP.  Cockpit may be the way forward.

As usual, I've found something else to add to my list of things to try when I should be handling more immediate needs. Oh well. Hope some of these leads are helpful for someone.

---

### Post by mag3lxub on 2023-07-13
> **TheFu said:**
> If you want an MS-Windows Domain Controller, perhaps paying MSFT for their software is the best answer?

[SIZE=6][COLOR=#ff0000]**NO!**[/COLOR][/SIZE]  I am done paying for Microsoft.  And now, with "subscription pricing,"   Unh Unh.     

> **TheFu said:**
> If you want to integrate Unix and Linux systems, then Linux/Unix methods would be the best answer.

I don't need to do Unix (although I did like Solaris 10 when I was working on Wall St. and managed a project that had large Sun Fire V880 and V1280 server machines implemented).  I simply want a Linux/Ubuntu domain Network with the same general functionality as my existing Windows domain network. Not necessarily "managed" by Windows, but just having "the same functionality."   And, an "Active Directory" component seems to be the critical element here, as Ubuntu Server has all the other components (DHCP, DNS, NTP, etc.).   

> **TheFu said:**
> If we put lipstick on a duck, it is still a duck.

Well, on Wall St, we put lipstick on "pigs,"  but I get it. :P At this point, I'm willing to co-exist with that "duck" if it facilitates the mission, long term.  

 > **TheFu said:**
> Management of LDAP on Linux kinda sucks, unless you have a separate tool just for that.  

And, I was hoping that Zentyal would have been that tool, but it appears not to be, at the moment.   So I'll have to see if I can work it with Generic Samba.  Like I said, "WINE" vs. "Bottles."  

> **TheFu said:**
> 
BTW, if you get a newer release of 20.04, you'll find they have newer kernels. My 20.04 systems are on
```
$ uname -r
5.15.0-76-generic
```
Get the Ubuntu Server 20.04.6 ISO.  Almost always, the newer _point_ releases of Ubuntu versions comes with a newer kernel to be installed.  

Do you know where I can find a .tar/ISO of Ubuntu Server 20.04 with that updated kernel? The only .tar's I can find are (like you said), 20.04.6 ISO, and that has only Kernel 5.4.  And the problem is, I won't be able to install that and then install the kernel update on top of it because I still won't have NIC/Internet access. The 20.04 tarball has to have the updated kernel already integerated.   


> **TheFu said:**
> 
BTW, my two main systems both have GUIs that didn't get driver support until 5.10.x kernels, so I'm fairly certain the latest 20.04.6 ISO came with 5.15.x kernels.  I just did a fresh, wipe-everything, install in May on one of the systems.

Like I said, if you can find a .tar ball that has the 5.15 kernel integrated, I would much appreciate it. Maybe I'm looking in the wrong places, but all I can see are Ubuntu Server 20.04.6 ISOs with 5.4 and no higher.

BTW, my current 22.04 Server install has 5.15 kernel.   Works like a charm. So, I'm strongly considering learning Generic Samba.

---

### Post by TheFu on 2023-07-13
If you aren't paying MSFT, why do you need/want AD or Samba?  Use NFS.

BTW, NTP is deprecated. It has security flaws which can be used to screw with system security.  Eventually MSFT will get that notice.

In the Unix world, DHCP/DNS/NFS and time keeping are each separate services.  They aren't part of a centralized system. Each is pretty light weight.

I don't remember doing anything special to get the 5.15 kernels installed on my 20.04 systems.  I did fresh installs, not upgrades.

We weren't allowed to use V880s where I worked due to their odd 3-cord power hookup requirements.   I don't recall the specifics around the V1280, but there was something odd with those too, so we didn't buy any.  We had thousands of larger and smaller Sun servers (Oracle).  Odd that your company was buying basically the only 2 models we weren't allowed to purchase.  We were buying E6800s and E12Ks as fast as Oracle could make them.  Also bought huge IBM and HP servers.  My projects were mostly Solaris and HP-UX systems.  We usually got 64-CPU servers and did virtualization.

The more I look at your needs, seems like Cockpit is the best solution.  I slept on it.

---

### Post by mag3lxub on 2023-07-13
> **TheFu said:**
> If you aren't paying MSFT, why do you need/want AD or Samba?  Use NFS.

For the Central User Authentication, Group Policies, Group rights/restrictions, machine management, etc. etc.  

> **TheFu said:**
> BTW, NTP is deprecated. It has security flaws which can be used to screw with system security.  Eventually MSFT will get that notice.

I don't care if MSFT gets the memo or not.  If it is being deprecated, what will replace it on the Linux/Ubuntu side?  It's still working in 22.04.  

> **TheFu said:**
> In the Unix world, DHCP/DNS/NFS and time keeping are each separate services.  They aren't part of a centralized system. Each is pretty light weight.

I know.   But AD (and Samba) use them (DNS and NTP). NTP being needed for Kerberos, etc. I recognize that I can do DHCP independently and will do so. 

> **TheFu said:**
> I don't remember doing anything special to get the 5.15 kernels installed on my 20.04 systems.  I did fresh installs, not upgrades.

OK, from where did you get your source ISO's for 20.04 (with the upgraded kernel)?  

> **TheFu said:**
> We weren't allowed to use V880s where I worked due to their odd 3-cord power hookup requirements.   I don't recall the specifics around the V1280, but there was something odd with those too, so we didn't buy any.  We had thousands of larger and smaller Sun servers (Oracle).  Odd that your company was buying basically the only 2 models we weren't allowed to purchase.  We were buying E6800s and E12Ks as fast as Oracle could make them.  Also bought huge IBM and HP servers.  My projects were mostly Solaris and HP-UX systems.  We usually got 64-CPU servers and did virtualization.

The more I look at your needs, seems like Cockpit is the best solution.  I slept on it.

As you were Oracle, we were Sybase.  We went with Sun Fire machines as Sybase DB servers (i.e. from SUN directly). I gather the ones you got were 240 volt 3-phase connections (hence, the (odd 3-cord hookup). IIRC, tje V1280 was a big as a refrigerator.... The V880's were 2/3rds that size.  So I can see the 240 volt 3-phase hook up.  

I'll take a look at Cockpit, but just to keep all advised, I actually have Samba 4.18 up and running on my server as a domain controller. It wasn't a hefty install at all.   I'll add DHCP a bit later.

---

### Post by MAFoElffen on 2023-07-13
That is a lot of posts skirting around the issue. 

As I remember, you downsized and have a requirement for file and resource sharing in your home office, right? You used to have Windows Small Business Server... You wanted something to replace it, with it being similar to, and the same kinds of functionality.

When it comes down to it, you do not really need "Need" a Windows Domain" like infrastructure to do that... Back then, you were convinced you needed something that mirrored and lauded that it was a one-for-one replacement of. Both TheFu and I tried to explain that it didn't need to be "the same" to be functional for you, when I recommended that maybe you should look at Zenytal. Sorry that Zentyal lags behind in it's own system base development. 22.04 has been out for 3 years now. How may months ago was that that we talked about that?

Overall, I think you are still stuck in the "Microsoft Server" mindset, that you think you need certain things in place, to be able to do certain things. Remember that I have to support customers with Unix, Linux and Microsoft Servers. You need the functionality to do things. Not the specific branding or the sales hype. You have a Small Business Model in a home office setting. You do not need to shell out $600 to $1400 on server licensing, which you would not use 98% of the features of to do what you need to do in that office setting.

You could de the same functionality with just separate Linux Desktops, using CUPS and NTS file shares. To share resources in Linux, you don't need a full blown separate server, that you need to maintain separately. You understand that right? It's changing your mindset to do whatever that different solution is. But it needs to be something that works for you, that can support what you need to do, and something that can be maintained.

As for Zentyal... Yes it is based on Ubuntu, and with being that, you could always install a newer Linux Kernel on it. That is another leverage of **Linux** itself, no matter what flavor of, the interchangeable pieces  and parts to make things work.

Starting over. "What functions do you need to accomplish in your home office?"

---

### Post by QIII on 2023-07-13
Building on MAFoElffen's post above, I would suggest the following to avoid the baggage already hung on this thread:

1.  Start a new thread,

2.  Ditch the MSisms and MS mindset.  Skip any mention of Microsoft or AD.  AD has 10,000 features of which you use, say, 3 - 5.

3.  Indicate that you have a Linux home office network and you want to be able to do x, y, and z.  Ask in layman's terms, not "like Microsoft AD"

4.  Ask how to implement those specific things.

5.  Accept the tuition of long-term Linux users absent any frame of reference related to MS products.

Just like Imperial versus Metric systems:  You don't need to constantly try to convert cups to liters.  Just use Metric recipes and throw out all of your Imperial measuring cups.

Using language as a metaphor for this, I speak German without having to translate from English in my head as I go.  

It'll be easier for everyone.

---

### Post by TheFu on 2023-07-13
> **mag3lxub said:**
> For the Central User Authentication, Group Policies, Group rights/restrictions, machine management, etc. etc.   

Let's take these one at a time.

_Identity Management_ - look for SSO. That's LDAP on Unix for the most part. I assume you aren't interested in running an x.500 directory.  I think Cockpit is probably the best answer for Ubuntu systems that host SSO for a network.  If RHEL is used, they have a specific product based on FreeIPA for this task, though I think Cockpit works there too.

_Group Policies_ - those don't really exist separately from normal POSIX groups.  Put users into a group and you can control where they can access, what they can run through file and directory permissions.

_Group Rights/restrictions_ - those are handled via chmod/chown and standard ACLs, not some central tool. I suppose we could put AppArmor or SELinux into this group, but that's seldom actually necessary outside of Govt or DoD work, unless someone has a specific audit checkbox that mandates SELinux is enabled. 
Of you want to split off administration into roles, not just "root/non-root", then "Role Based Administration" is something that the commercial UNIX vendors have had for about 2 decades.  I think SELinux can do something similar, but I've successfully avoided that and it doesn't deploy to Ubuntu or Debian systems, so you've got the wrong distro if that is a goal/need.  

_Machine Management_ can be anything. But if you seek a way to keep a machine configured and patched in specific ways either as a group of 1-500 other systems, or specialized as a single machine, most Unix companies do this with a DevOPS tool like Ansible, Chef, Puppet, CFEngine or with their home-grown ssh scripts.  Each week, I use a script that leverages ssh to patch each of my systems - local and remote. It is easier to have that script than it is to use Ansible, at least for me.  I use Ansible and have been through the pain that is Chef and Puppet training.  Give me Ansible any day of the week over those other options.  5 or 5000 systems, it doesn't really matter to me.  I'll just review the logs from the interactions anyway.

If the system has a remote console connected via serial port, and there's a monkey who can swap a flash drive or DVD, I never need to visit the location.
It is a different mindset.

BTW, I use these terms in this way:
[LIST]
[*]UNIX = commercial UNIX - Solaris, HP-UX, Irix, Digital Unix, OSF, AIX are examples. There are others.
[*]Unix = any Unix-like OS.  BSD, UNIX, and all Linuxen fit. Sometimes, ?mostly?, MacOS fits too. Same for Android.  At the shell, Android is Linux and Unix.
[*]Linux = Only works for Linux and probably will not work on Unix.  For example, dd has different options on MacOS, so the Linux version is Linux specific.
[/LIST]

MAFoElffen - I think you have a number of typos in your last post, but I could be wrong.

---

### Post by mag3lxub on 2023-07-13
> **MAFoElffen said:**
> That is a lot of posts skirting around the issue. 

As I remember, you downsized and have a requirement for file and resource sharing in your home office, right? [COLOR=#0000ff]** No, I never _*downsized*_ at all.**[/COLOR]  

You used to have Windows Small Business Server... You wanted something to replace it, with it being similar to, and the same kinds of functionality.  [COLOR=#0000ff]**No, I had (and still have) Windows Server 2003. It's still configured and works as a Primary Domain Controller). Still, it being 20 years old, it's time to replace it. And I no longer wish to pay for Windows based products... especially pay "subscription" prices. **[/COLOR]

When it comes down to it, you do not really need "Need" a Windows Domain" like infrastructure to do that... Back then, you were convinced you needed something that mirrored and lauded that it was a one-for-one replacement of. 

[COLOR=#0000ff]**If that's what I said, then let me correct it now.  I agree, I don't **[/COLOR][COLOR=#ff0000]**_*need*_ **[/COLOR][COLOR=#0000ff]**a Windows like "domain structure."   I **[/COLOR][COLOR=#ff0000]**WANT**[/COLOR][COLOR=#0000ff]** IT!  I want it because it's what I did during my professional career and I want to stay in the game.  Why do some women need 100 pairs of "Minolo's..."  (or, to be fair, some men needing 100 pairs of "Jordan Retros" )?  Or  17 different sports cars? The real truth is, they don't!  But they want them....  because they like them.  I like keeping my home network the same as the ones I did in my office.    **[/COLOR]

Overall, I think you are still stuck in the "Microsoft Server" mindset, that you think you need certain things in place, to be able to do certain things.  [COLOR=#0000ff]**See above.**[/COLOR]

As for Zentyal... Yes it is based on Ubuntu, and with being that, you could always install a newer Linux Kernel on it.  [COLOR=#0000ff]**Actually, I can't.  Not unless someone finds me an Ubuntu Server 20.04 ISO that has a kernel level >= 5.9 already built in, which is the 1st kernel level that supports my internal NIC card.  The only 20.04 ISOs I can find all have kernel 5.4.  That won't support my NIC. Which means, I can't download any newer kernel version to overwrite it!. **[/COLOR]


That is another leverage of **Linux** itself, no matter what flavor of, the interchangeable pieces  and parts to make things work.

Starting over.

No, no need for that (starting over).    I have my answers and I'll be ending this thread.   Thank you.

---

### Post by MAFoElffen on 2023-07-14
The Ubuntu Desktop 20.04.6 LiveUSB will install to your computer with the HWE stack, 5.15 series kernels. If what you say is true, then those are newer than Kernel 5.9. Just ensure that when you setup the hostname, that it is less than from 4 to 14 characters long. Longer will crash Zentyal when it installs. Also, ensure that you setup it with a static IP address.

Then install Zentyal on that via
```

sudo apt update
sudo apt dist-upgrade

```
You have to do this. If their script sees that there are any pending updates, it will exit telling you you do not have your system up to date, with it's updates...
```

mkdir ~/Scripts/
cd ~/Scripts/
wget https://zentyal.com/zentyal_installer.sh
sudo chmod u+x zentyal_installer.sh
sudo ./zentyal_installer.sh

```
When it asks: "Do you want to install the Zentyal Graphical environment? (n|y)"... Answer <n> for no. The desktop edition already has a GUI installed.

When it finishes, start Firefox and in the address bar, go to 
```

https://localhost:8443

```
Login with your credential installed in the system already, install and configure the components.

I remember their installer likes to wack the network settings, if you don't set them up during their install/config, so do not skip that step.

It works, for them and their system. On a kernel newer than you say you need.

Complaints, finger pointing and rants, are not good methods to try to get help from anyone.

---

### Post by mcdonnell155 on 2023-07-14
You can download hwe kernel debs and all dependencies from packages.ubuntu.com to install with `dpkg` e.g. [https://packages.ubuntu.com/focal/linux-generic-hwe-20.04](https://packages.ubuntu.com/focal/linux-generic-hwe-20.04)

Or you can buy a USB/temporary NIC and do it the normal way...

I built samba from sources across a wide period of time (same windom through samba4 beta releases 'til like 4.14), it is very stable upgrade process. Works very well for group policy.

---

### Post by mag3lxub on 2023-07-15
> **mcdonnell155 said:**
> You can download hwe kernel debs and all dependencies from packages.ubuntu.com to install with `dpkg` e.g. [https://packages.ubuntu.com/focal/linux-generic-hwe-20.04](https://packages.ubuntu.com/focal/linux-generic-hwe-20.04)

Or you can buy a USB/temporary NIC and do it the normal way...

I built samba from sources across a wide period of time (same windom through samba4 beta releases 'til like 4.14), it is very stable upgrade process. Works very well for group policy.

Thank you!  Thank you so much!

The thing that fixed it for me was installing the HWE version. I went back to my original 20.04 ISO and the HWE version did appear in the start up/install menu. That's what I was missing/not connecting.  I now have 20.04 installed with kernel 5.15 and full NIC access with a fixed IP. I can now proceed with DHCP server install and the Zentyal 7.0 install and all the other things. 


I also appreciate your kindness in how you responded to my query.   I know it might have seemed to some as though I was "Complaining, finger pointing and ranting."  And I do apologize for that. It was never my intention  My responses were, simply, a reaction to my mutual perception of "condescension" from some of the experts, here. Yes, I might be relatively new to the Linux/Ubuntu world and. to a lesser extent, the UNIX world (I do have a bit of professional experience there), but I was an IT professional for over 45+ years (starting with IBM Mainframes and moving on to Windows Client/server).  I ran a my own computer consulting business for 10 years, where I did that kind of networking stuff in Windows. I'm retired now, but still do things like these Ubuntu builds to stay "in the game."  And, yes, I most likely don't need a Windows like domain environment at home.  I just want it, is all.  I want my home network to look like the same things I did for my work.   That's what I think may have been misunderstood, here...  why I wanted to do it.    And the fact that I'm transitioning from Windows to Linux/Ubuntu and wanting the same functionality/environment as Windows was only incidental. If I could have stayed with Windows, I would have.  But I just couldn't justify paying for Windows anymore. And I wanted to continue to challenge myself by trying new things. Looks like a Windows like domain environment on Linux/Ubuntu served as a worthy challenge.  Challenge accepted!


Believe it or not, I do have the utmost respect for the Linux/Ubuntu experts on this forum and for their knowledge/experience. All I ask in return is to be treated with similar respect for my knowledge/experience. I may be a Linux/Ubuntu "newbie,"  but I'm working on it.

---

### Post by MAFoElffen on 2023-07-15
I came from that same world... DEC and IBM mainframes, workstation controllers, and terminals. That is where I learned first learned XServer and Unix. Along with that, Windows 1.0, and IBM PC's. And how I used to not try to let people I knew how to write COBOL. Some things, in how they work, are still basically the same, but just applied differently. My niche as an IT Consultant was to show people how to make them all work together.

Now I show my age. LOL. We have a lot in common.

---

### Post by DuckHook on 2023-07-15
I daresay that practically all of the oldies (is that the acceptable converse of "newbies"?) on this forum are thoroughly versed in Windows. My own experience is reflective of yours too, as are those of MAFoElffen, TheFu, QIII, many others.

I recognize and accept that you are committed to reproducing your Windows environment in Linux. Not trying to "talk you out of it" and by no means intending to be condescending. What follows is just my personal story.

Though I'd dabbled in Linux for years (even in my Windows days), I didn't really start using Linux until my retirement. Up to then, I was a confirmed hard core Windows power user. My first foray into real Linux application was an attempt to reproduce the environment in which I was already comfortable.

So, almost identical story to yours: Samba, AD, beefy all&#8209;in&#8209;one server, GUI admin, NTFS, Exchange equivalent, all my eggs in one big unwieldy rickety single&#8209;point&#8209;of&#8209;failure basket. I too tried Zentyal as a replacement for SBS. In other words, I tried to run Linux like Windows.

But over time, it gradually became brutally apparent: reproducing Windows was a mugs game because (there's no nice, diplomatic way to put this) Windows sucks.

It foists obsolete technology on us, is smothered in kludges (because that's the only way to keep it grinding along), settles for third rate stuff, is full of gaping holes thereby requiring workarounds, is appallingly insecure, runs like a snail on tranquilizers, is an obese resource pig, is completely inflexible and hides all of its ugly warts by distracting us with a pretty GUI.

The sad thing was that, while I was using Windows, I thought all of these shortcomings were normal. So, I actually insisted on dragging them with me into Linux. I look back now and I shake my head and sigh at that old me.

I have no idea how your own experiences will unfold. You have every right to explore those and formulate your own experiences. I just want to note that when the old&#8209;timers on these forums try to dissuade you from reproducing your Windows environment, we are not being condescending, nor are we overlooking your years of hard&#8209;earned expertise. We are just trying to spare you the pain of our own missteps.

---

### Post by TheFu on 2023-07-16
I was never a Windows Admin outside of a small workgroup and that was pre-AD.  I did get training in Netware 3.x and 4.x along with NDS, which is what we had before LDAP made it easier.

I've been a UNIX and Unix admin since 1994, however.

---

### Post by mag3lxub on 2023-07-16
> **MAFoElffen said:**
> I came from that same world... DEC and IBM mainframes, workstation controllers, and terminals. That is where I learned first learned XServer and Unix. Along with that, Windows 1.0, and IBM PC's. And how I used to not try to let people I knew how to write COBOL. Some things, in how they work, are still basically the same, but just applied differently. My niche as an IT Consultant was to show people how to make them all work together.

Now I show my age. LOL. We have a lot in common.

Especially, the "age" part.  :P

I forgot to say I did start with DEC as well, but that was in High School. Our public HS was one of the first in the area to acquire a DEC PDP-11/40, built by one of their OEMs, "Educomp" in Hartford, Ct. (so it actually didn't say "DEC" on the paneling).  At the time, it was running RSTS V4A for the general student population (with BASIC language). Sometimes, they'd bring that down and run a FORTRAN batch system on it (previously, we had an IBM 1130 which did FORTRAN so we had to let them have that functionality). 

From then, it was onto University.  They were a "CDC" shop.  Initially a CDC-6400, mainframe and then upgrading to a 6600 while I was still there.  All batch work.  Old style IBM keypunch machines, keyed for ASCII and not EBCIDIC. Frustrating as you'd have to repeat a card if you made just one mistake.   There was an IBM S/370 138 there, but it was for the "Administrative Data Processing" unit as well as it maintained the Library's electronic catalog and book checking out system.  It ran DOS/VS with Power. I worked as an operator there for one of my college jobs and made friends with the prof who taught COBOL at the school and let us use that machine to do our projects. He was also the head of the Library's IS dept.  Eventually, the Library got their own IBM 4331, and transferred all their work to that machine. The ADP unit got a 4341, which they filled to the brim with their work, running 24hrs, 3 shifts.   Had I stayed (I was graduating), I would have done 1st shift work on the second shift, instead of Library work. The 3rd shift (midnight) was for processing Alumni operations. I discovered later that the most "secret/confidential" thing processed at ADP was not the University Payroll or Student Registration / grades database. It was the "alumni contribution" system and database. Only one operator there, overnight.  No other staff.  

I visited the main computing center several years after I had graduated (the CDC one) and it had been totally revamped with client server machines.  The CDC mainframe and keypunch stations were gone.  Funny, but I recall starting a new job and going to mainframe training classes in a system called TELON, a CICS COBOL facilitator. It generated CICS COBOL code, maps, etc. etc. a lot easier.  That training took place in North Quincy, Mass, and I stayed in Boston while training there. I had a chance, and got over to Boston's "Computer Museum."  Couldn't pass that up, although I probably should have.  No more than 30 ft. or so after I entered the building, I saw the first exhibit. It was the very CDC-6600 I used in college (maybe not the "exact" one, but...)!  Talk about feeling one's age!  

But I digress.  I was able to get Zentyal 7.0 installed (BTW, I've discovered a ver. 7.1 now(**[COLOR=#0000ff]wget [https://zentyal.com/zentyal_installer_7.1.sh](https://zentyal.com/zentyal_installer_7.1.sh)[/COLOR]** )), but I think I made that mistake you mentioned about rebooting before re-configuring the network settings.  I will start over again with 7.1 and make sure I configure network before rebooting. A lot of the documentation and Youtube videos mention that as well. I think I will also install Ubuntu Desktop first as a GUI, before I try Zentyal again, rather than try to do things in tty mode. It's a good thing I found "Timeshift" as a backup/restore utility before I started doing all of this.  It works like a charm and restored everything not on my /home directory (which I have on a different physical drive). Once restored, the network connections/activity came right back.  So I'll try again, later today, after some prep work.

---

### Post by mag3lxub on 2023-07-16
> **TheFu said:**
> I was never a Windows Admin outside of a small workgroup and that was pre-AD.  I did get training in Netware 3.x and 4.x along with NDS, which is what we had before LDAP made it easier.

I've been a UNIX and Unix admin since 1994, however.

At the same company where they trained me in TELON (see above), they were getting on to Novell Netware 3.X and then migrated to 4.X while I was there.  IIRC, we were one of the first to use the "[Wallongong Group]("https://en.wikipedia.org/wiki/The_Wollongong_Group")" suite of network software (out of, of course, Australia).  This was way back when TCP/IP was just coming to fruition.

---

### Post by mag3lxub on 2023-07-16
> **DuckHook said:**
> I daresay that practically all of the oldies (is that the acceptable converse of "newbies"?) on this forum are thoroughly versed in Windows. My own experience is reflective of yours too, as are those of MAFoElffen, TheFu, QIII, many others.

I recognize and accept that you are committed to reproducing your Windows environment in Linux. Not trying to "talk you out of it" and by no means intending to be condescending. What follows is just my personal story.

[SIZE=6]...[/SIZE]

I have no idea how your own experiences will unfold. You have every right to explore those and formulate your own experiences. I just want to note that when the old&#8209;timers on these forums try to dissuade you from reproducing your Windows environment, we are not being condescending, nor are we overlooking your years of hard&#8209;earned expertise. We are just trying to spare you the pain of our own missteps.


Totally understood, and appreciated.   And I, as well, feel all the imperfections of the Windows environment. Witness all the "security updates" we have to apply that never seem to end.  I'm still using Win 7, 64 Ultimate as my "production" desktop, and I'm still getting security updates, even post EOL.   

I guess I'm the kind of person that does need to "explore and formulate my own experiences."  And, yes, make those same mistakes.  Because I've found over the years that some of the very best lessons I've learned and that have stuck with me all this time are from when I make those mistakes.  Hopefully, by now, I'm at a point where my mistakes aren't all that critical... that they won't cause significant damage or $$$ loss... that making those mistakes isn't a "**[COLOR=#ff0000]OH HOLY CRAP[/COLOR]**"  thing.... just an "[COLOR=#ff0000]aw crap[/COLOR]" thing. :eek: Yeah, it may take extra time and, perhaps, a few $$$, but I learned valuable lessons.  Yes I may, at some point, regret the decision to clone my Windows domain environment into Linux/Ubuntu with Linux/Ubuntu tools.   For now, I'm still willing to fight for it.    


I am curious, though.  How would you all replicate all the general functionality that Windows "Active Directory" (or Zentyal in this case) offers in native UNIX/Linux?  Certainly, things like DHCP and DNS, etc,. are already there.  But what about a central user repository, group policies, single sign-on, and the like?  Would you try an LDAP implementation of some kind? Radius?  Kerberos?

Or would you change the paradigm to something else?

---

### Post by TheFu on 2023-07-16
> **mag3lxub said:**
> At the same company where they trained me in TELON (see above), they were getting on to Novell Netware 3.X and then migrated to 4.X while I was there.  IIRC, we were one of the first to use the "[Wallongong Group]("https://en.wikipedia.org/wiki/The_Wollongong_Group")" suite of network software (out of, of course, Australia).  This was way back when TCP/IP was just coming to fruition.

TCP/IP was around since the 1970s, actually 1969.  The fact that Netware and MSFT didn't add it to their stacks for 20 yrs is a different issue.  UNIX had it for decades before then. 
My DEC workstation ran both IP and DecNET stacks in 1992.  I remember struggling to get enough free RAM below 1MB to load IP into MS-DOS.  By  1994, it was clear that IP was the preferred network stack, so some places did still use token ring to get slightly better performance, with the liability that if any NIC in the ring had a failure, all systems on the ring would lose connectivity.

I suppose "fruition" could depend on the point of view of the person viewing. If you were deploying Netware, then you may have thought that SPX/IPX was **THE** answer.  

At the time, one of my jobs used protocol changes as a security feature to wall off 2 different IP networks, by having an SPX/IPX network between them.  Because it didn't route,  the only way to move a file between those 2 IP networks was to physically sit behind a workstation connected to the inner Netware server NIC and move the files onto the secured IP network. It was a better solution than using tape, which was how we introduced everything else into that network, which required physically using a specific machine, waiting a day for someone else to download and scan everything for MSWindows viruses (MS-Windows wasn't allowed on the "secured" network, so that was useless), then upload the files to a different computer on a different network.  I remember my customers being unhappy that we couldn't just copy programs over the same way we did data and have it available in an hour.  But I wasn't going to lose my job or go to jail for not following procedures, not for them or anyone else.  If they didn't like that it took a day, then they could get their security procedures relaxed - which were in out contract to be followed.  My client had a lot of pull in the organization, but not THAT much pull to get security processes removed.

---

### Post by TheFu on 2023-07-16
> **mag3lxub said:**
>  
I am curious, though.  How would you all replicate all the general functionality that Windows "Active Directory" (or Zentyal in this case) offers in native UNIX/Linux?  Certainly, things like DHCP and DNS, etc,. are already there.  But what about a central user repository, group policies, single sign-on, and the like?  Would you try an LDAP implementation of some kind? Radius?  Kerberos? 

Did you not read the replies above which spells out the Linux way?

As for Radius, I use IPSec VPNs instead.  When I deployed remote access for 22K users, we used hardware specific to the task tied with RSA SecurID tokens.  We also deployed Blackberry devices to those same users, but placed them onto a specific network, not the public internet, so they could get their next jobs. 

At home, I use wireguard for all my wifi connected devices to have access to the rest of the LAN. I don't trust wifi security.  I was trying to deploy an overlay mesh network, but it seems my routers are too smart and don't allow the trick the mesh VPN uses to work.  Most home/consumer routers wouldn't block this access, it seems. I was just "lucky", I guess, so wireguard was the best answer.  2-20 yrs ago, I was using openvpn instead, but wireguard is much cleaner, faster, and lighter to deploy.  This morning I wanted to watch some sports that are blocked in my area, so I spent 10 minutes renting and setting up a wireguard server at a VPS with exit nodes around the world.  Watched the competition and saw it was $0.02 for that time.  The next few days, I'll setup and tear down the wireguard system as needed to catch a few more competitions at the world championships.  I suppose I could pay for a VPN service for 1 month - $5-$10 - but this way, I'll have a script that does the wireguard deployment working and will probably get everything down to less than 1 minute for a new VPN/Proxy to be created and running.  I think the VPS cost is $0.007/hr.  Actually, the biggest part of the hassle is deploying a new VPS with their slow point-n-click interface and because I never want to pay extra for their backup or to have IPv6 or a few other addons, I think I'd like to automate the new server deployment aspect too. It will still take about 30 seconds for them to set it up and tell me the IP address, but at least they preload my ssh public keys.

---

### Post by DuckHook on 2023-07-16
> **mag3lxub said:**
> Or would you change the paradigm to something else?
Your question is an excellent one, but you need to recognize that it presupposes that Window's AD paradigm is both unique and good. Both of these presuppositions are false. I've already touched on how awful Windows is in almost everything they do. There's no reason to believe otherwise about AD.

Before getting into the details, I'll answer your question succinctly:

[B][I]I would change the paradigm to one that is native to Linux. That way, you run Linux by leveraging its own best strengths rather than compromising it from the outset by trying to force its square peg into MS's round hole. In my experience, nothing good has ever come of trying to run things that way—in any walk of life—computing is no different.
[/I][/B]
Details follow (with a caveat):

***Caveat***
I am a Linux power user. I do not have the training or the chops to be a sysadmin or netadmin. There are others on this thread and more on this forum who can run rings around me in the technical department. So take what follows with a liberal dose of salt.
***End of weasel words***

When I went from Windows SBS to Linux, I too thought that I would have to reproduce all of that AD functionality. It turns out that I didn't.

Take group policies as an example. The reason that Microsoft makes such a big deal about this aspect of AD is that Windows' native group policy stinks. In fact, it is non&#8209;existent. The NTFS/SMB stack does not lend itself to group security. This is because Windows never started out as a secure multi&#8209;user OS. It was a dodgy single&#8209;user OS that didn't give a hoot about security. MS did what it always does: instead of rebuilding the NTFS/SMB stack to have native security, it slathered on a workaround (AD) to lend it functionality that it was not natively capable of. The result is bloated, inefficient and fragile, but they could now pat themselves on the back and say that they have it.

Contrast this to Linux's native ext4/NFS stack. It has group security built in from the outset. It's true that it's a bit unwieldy tweaking group permissions for a large and varied assortment of files for many users, but the point is that the infrastructure already exists natively. No need to slather a workaround on top of it. The result is lean, efficient and robust because it was thought out and designed properly from the outset.

When I retired, it quickly became clear to me that I didn't need all of that atrocious Windows&#8209;brainwashed overhead. Sure, there are tools that will make working with Linux permissions and groups even easier, but when the user base consists of just me and Mrs DuckHook, fumbling around with those tools is more trouble than they are worth. I simply set both of our group masks to the same group and it's done. Easy&#8209;peasy. No muss, no fuss, no pain.

Now take single sign&#8209;on. What did I really need this for? It turns out that I didn't. Linux security is more robust than Windows precisely because it takes challenge/response seriously. So, repeating a username/password combo once a week to update my server is not really a hardship. Besides, Linux has made many maintenance functions easy: I ssh into my servers using shared keys, so passwords aren't even needed for rote tasks. And, using a password manager, it is child's play to administer as many challenge/response combos as needed—into the hundreds or thousands if necessary—so the whole point of single sign&#8209;on has been rendered moot to me.

The benefits are enormous. For a tiny bit of extra effort, I have greatly enhanced security. By training myself out of Window's bad habits, I have built up extra layers of safeguards against the bad guys. I now have security in depth at the small price of giving up a bit of false single sign&#8209;on convenience. Why do I call it a "false" convenience? Because a good friend of mine was compromised when his single sign&#8209;on was extracted from him through a clever social engineering scam. The hell and expense that he went through trying to recover from this breach gave the lie to how "convenient" single sign&#8209;on really is.

If you want to do things the Linux way, then it does indeed require a paradigm shift. 99% of that shift will be for the better, but from a Windows user's perspective, that 99% is hidden while the 1% that will initially inconvenience them looms large. It's a perverse state of affairs, but unavoidable.

My own experience with the MS SBS to Linux transition was challenging. For about a year, I felt like I was drowning and I clung to what I knew as sort of a flotation device. But I gradually came to understand that the trick to making the transition was to get my head wrapped around the idea of simplifying. Here are a few general principles that helped me:

The whole MS SBS model is broken and bad, especially in the context of Linux. The reason MS touts it is because users have to pay dearly for every server licence in the proprietary world. Therefore, artificial economy dictates that all functions be concentrated into one box. But in the Linux world, server licences are free. You can run as many boxes are you want without paying a dime. Freed from this economic tyranny, the real power of Linux manifests. You should spread your workload among many machines for all sorts of benefits:

Each machine now runs only one function, but runs it well:

[LIST]
[*]This reduces the work load so much that you can now use cheap reconditioned machines effectively.
[*]Cheap machines also mean that you can now afford to buy multiples for redundancy. My mirrored file servers are two Western Digital MyBookLives that I picked up from ebay for $40.
[*]No more single point of failure, whether mechanically, operationally or security&#8209;wise. My DNS, DHCP, file server, backup, private cloud, VPN, mirroring services are spread among more than half a dozen machines, all costing me less than the price of my single old SBS server.
[*]Running only minimal single&#8209;task machines makes for simple admin and very low attack surface (but you have to get used to administering servers without GUIs).
[/LIST]

I don't need Zentyal masquerading as SBS—not because it is difficult to implement—but because it is a bad paradigm to start with.

---

### Post by mag3lxub on 2023-07-17
> **DuckHook said:**
> Your question is an excellent one, but you need to recognize that it presupposes that Window's AD paradigm is both unique and good. 

 I make no such presupposition. The Windows AD paradigm, simply,  is what it is... It's all that's there, AFAIK. If something comes along that's better, I'll certainly look into it. Apparently, I need to read the upper posts in this thread a bit more carefully and I might find something... We'll see. If it doesn't allow things like "Group Policies" and the like, I might have to stick with what I have, for now. Or, perhaps the elimination of group policies, etc. is part of the paradigm change.  


> **DuckHook said:**
> I don't need Zentyal masquerading as SBS&#8212;not because it is difficult to implement&#8212;but because it is a bad paradigm to start with.

And, after 24 hours of hard work, all for nothing, I would agree with you.

I actually did get Zentyal 7.1 up and running on my Ubuntu Server 20.04, after first installing Gnome desktop for 20.04. I followed all the instructions, set the Zentyal networking configs all immediately after installing, and it worked great! 


And, then, I rebooted.  :(



The system froze just before the Gnome Graphical Environment engaged.  All I got was that one little cursor line at the top of the text screen. And that's where it hung after each reboot attempt.   Normally, you'd get that little cursor but within a minute or so, it would disappear and be replaced by the arrow cursor in graphic mode, followed by the Ubuntu login page.   Not happening.

I knew I'd have to rebuild the machine to get anywhere, so I went ahead (thinking there must have been some conflict using Zentyal), and I rebuilt the machine with Ubuntu Server 22.04 (Jammy Jellyfish) with the intent of going direct with Samba 4.8.  And, lo and behold, that has worked! I have 22.04, Gnome desktop and Samba 4.8 all installed and working properly. I've done the reboot test and all processes restarted. I'm using Samba's "Internal DNS" forwarded to  a couple of known name servers. I've installed isc-dhcp-server  for dhcp and, after some "negotiating with the config files"  (the less entered the better), it is up and running along with all the other components.  And, all have passed the "reboot" test.  It's working perfectly!


Over the next few days, I'll be migrating my clients over to the new server and creating users, etc. etc.  The goal being to decommission the old Windows Server 2003 machine before month end.   


Finally, it's done. I'm glad I didn't give up!

---

### Post by TheFu on 2023-07-19
Unix systems don't have group policies, so it doesn't make sense to have special tools to manage something that doesn't exist. It is a philosophical difference.  Unix is designed so that administration things can only be changed by administrators and that users should be allowed to do almost anything on the system, provided it doesn't harm other users or impair the system in any way. 

The system cannot tell if what a user is requesting is pure genius or pure stupidity, so it allows both. End-users cannot do anything to harm the system, in theory.  Some changes to increase convenience have changed that slightly, but those things can be disabled by a competent admin.  For example, allowing end-users to mount any storage is a terrible idea and shouldn't be allowed. The power to mount is the power to destroy.

Another example. There isn't any "control panel" for normal users in Linux, so there's no need to hide it from them.  There aren't any system settings that normal users can modify, so there's no need to prevent them from doing so.  Some files which contain sensitive information are unavailable to normal users, but many files don't have any sensitive information, so viewing is perfectly fine.  If an end user tries to do things they aren't allowed, they will usually see an Error -13, permission denied.  Error numbers are system-wide and stored in a header file, of you'd like to look them up.

There's no registry in Unix either.  There are personal DBs which hold settings, but those settings are per user and users should be allowed to control their own per-application settings, right?  Many programs still use text config files rather that hiding settings inside a DB of dubious usefulness.  OTOH, if it always safe to completely remove those DBs and start over fresh.  gconf and dconf are example programs that users can run to modify and view settings for selected programs.

Users are allowed to do anything that won't harm the system, smart or not. They aren't coddled. That's also part of the Unix Philosophy.

Users can choose to work together, if they like and are in a shared Unix POSIX group.  This is handled through file permissions.  File permissions are the cornerstone of all Unix system security. After all, almost everything is a "file" on a Unix system, so controlling permissions on files means controlling nearly everything.  Devices are files.  directories are files. System settings on a running system are shown as files.  By controlling the permissions to a file, access levels for the information or to modify it is possible. It is quite elegant and this idea applies to all Unix-like OSes.   

The only thing that isn't a file, is a running process.  Everything else is a file.

As for how to make settings the same across 1, 5, 5000, 50,000 machines, there are many ways.  In the 80s and early 1990s, we'd use **rsh** to run commands across however many systems we needed them run.  In the mid-1990s, **ssh** replaced rsh and security was vastly improved.  ssh is how Unix-like computers communicate between each other world-wide.  It is how remote administration is performed and using scripts, it is possible to manage 1, 5, 5000, 50000+ systems around the world.  

Old time admins have been scripting stuff for many decades.  The last 15 yrs, "DevOPS" tools have been marketed as the way to manage many systems. Sometimes these tools do simplify management and other times, the tool brings more problems than it solves.  I use a mix of custom ssh scripts and Ansible to manage my systems.  My custom scripts aren't usually very complex.  They pass in a script on stdin into a shell interpreter on the other system over ssh then run the script. It is a basic admin technique and doesn't require anything on the remote system besides ssh and the shell and common commands that are part of the distro being managed.  Super light Linux distros may not have all the commands used, but most do.  Effectively, this method has been part of Unix administration since the 1970s.

```
ssh $RUSER@$REMOTE 'bash -s' <<CLEANUPSSH
# Do something
CLEANUPSSH

```
That's the model. Just write the commands to be run on the "REMOTE" system between the two CLEANUPSSH markets. For people new to Unix, often the hardest part of this is thinking multi-user, since the "RUSER" will be the userid all commands run under.

---

### Post by MAFoElffen on 2023-07-19
I have been both a Linux and Windows Admin.

I apply security policies in the same way on both, in methodology.

The basic methodology is this:
In Domain, you want a single source to validate users, and groups, such so you can access files and application services. I use 3 services for that: Kerberos, LDAP, DNS. That gives me single sign-on and access authentication. Basically you have users that are members of groups. I apply security and access to groups. The I make Users members of those groups. I administer ACL's based on group access. If I do it that way, then it is just easier to manage.

With that in place, I can share resources and files from a central location or pool of resources.

No matter what OS we are talking about, that is what that boils down to. That is the underlying methodology.

This effort would be for access "many users" enterprise wide (10's to 100's to thousands)... Just how many Users are you talking about for your home office? Because if you are only talking about 5-10 users, then you are doing a lot of effort that is very much overkill. That's like buying a Ferrari, when you work location is two blocks away. You might not even get it into the top-gear...

---

### Post by MAFoElffen on 2023-07-19
List out your requirements...

I have taken offices using Windows and extended WorkGroups local policies to their limits and the Small business ran on just that. I have done the same with just Desktop Linux machines. The only thing different from having a server with central administration, was that there was no single-login, an no hardened, forced, central admin.

So the abilities are there, with whatever you use, to scale. The big differences are with Linux, you are not paying for the licenses, and you are doing the same things 'differently'...

I could go into details on Unix, Linux, Windows, MacOS... But why? The term "Domain" is not a Microsoft trademark, it is a methodology...

My niche as an IT Consultant was in providing multi-platform solutions that work together as one. My job isn't to sell someone a product or brand. I sell solutions that fit their needs. I don't really care what they use, as long as it fits what they want to do.

I prefer a Linux Solution. There is not anything I can't do with that. Windows, VMware, MacOS... Both Windows and VMware solutions are costly. MacOS solutions are costly, limited, and are not long-term without hardware turnover. Then I have to add other things to get there with them, or use other methods for them to be able to.

Saying that-- I don't care what you use... As long as you can do what you need to do, and you can support your infrastructure in some kind of way, even if that way is by paying someone for help when needed. I think it is smart and can agree with your reasoning for trying a Linux Solution. I don't feel like you need all the bells and whistles of something like Zentyal, but Zentyal has a lot of things that will make what you are trying to do easier for you, your skill level, and what past experience you have. It has fill out forms in an HTTPS GUI screens that lead you though configuring things... Me? I usually default to just editing the config files manually in an editor. But that is the world I come from, my experience and skill level.

If you knew how to do that like me, then you wouldn't be looking at Zentyal... You would just do it. Then you would know the pieces you need to do "things." I recommend Zentyal to users that are new to Linux, and have a Windows background, who do not yet know how to translate what they know into Linux terms. I don't think Zentyal 'scales' well above a Small Business infrastructure. But then again, that depends on what they are trying to do. For those larger, I recommend other solutions.

You haven't answered many questions on what you need to and want to do, and how many users... That would dictate what you "really need".

---

### Post by mag3lxub on 2023-07-20
> **MAFoElffen said:**
> List out your requirements...

If you knew how to do that like me, then you wouldn't be looking at Zentyal... You would just do it. Then you would know the pieces you need to do "things." I recommend Zentyal to users that are new to Linux, and have a Windows background, who do not yet know how to translate what they know into Linux terms. I don't think Zentyal 'scales' well above a Small Business infrastructure. But then again, that depends on what they are trying to do. For those larger, I recommend other solutions.

You haven't answered many questions on what you need to and want to do, and how many users... That would dictate what you "really need".

I haven't answered the questions because the number of users (at this point) is just "one.."  me.    As stated earlier, I don't "really need" any domain like paradigm at all...  I just want it, primarily for the intellectual challenge of doing it and keeping it well maintained, like I did during my professional career.  Also, for the challenge of doing it in a new "OS" environment (Linux/Ubuntu vs Windows) and yielding as similar a result as I can.  

I have proceeded to "abandon" using Zentyal, as you suggest above. At present, I am "up and running" with Ubuntu Server 22.02 with Samba-AD-DC 4.5 for the "Active Directory" component, as well as "ISC-DHCP-Server"  for DHCP running independently on the same machine (although I understand that may deprecate shortly to their "Kea" product.  I configured Samba with the "INTERNAL-DNS" back end for the AD operations.  But that won't be a full solution for regular DNS queries as it can't do things like "recursive" DNS queries. So I either change Samba to the "BIND9-DLZ" back end, or I build a separate DNS server, potentially a separate physical machine (since I don't think Samba in INTERNAL-DNS mode can co-exist with a separate, independent DNS Server on the same machine sharing the same IP). At present, I'm still using my old Windows Server 2003 server for regular DNS but I need to change that soon. I was thinking of installing the NTP service for time management,  but I will stick with "Chrony" as it works well with Samba.  



That's where I'm at, right now. My next big question is, should I switch to "BIND9-DLZ" DNS back end in Samba, or build a separate, independent DNS server? If separate, can it co-exist on the same Ubuntu machine that hosts Samba, or should it be an independent server machine (which will serve as Samba's DNS "forwarder")?


Thanks all.

---

### Post by MAFoElffen on 2023-07-20
I came from a world where I was directed to use Bind9... I hear the Dnsmasq is faster and easier. I know that TheFu talks about it allot, so he must know a lot more about that than I on that.

What I would do? In the past I did separate machines... Then consolidated my 14 servers into one machine, using a VM host, with VM Server Guests, with a bridged NIC so it had access to the host network. That was around Ubuntu 10.04 LTS(?) That is what got me interested in virtual host systems, and in KVM specifically.

I think TheFu does some of the same, but also uses LXD containers for some of his services. So, he also seems to virtualizes his needed services.

Yes. I am an old Techie. I can understand the "wanting a challenge" kind of concept. I don't 'require' what I have here, or the ways I still do things. But it is fun, challenging, and fulfilling to me.

---

### Post by mag3lxub on 2023-07-21
> **MAFoElffen said:**
> I came from a world where I was directed to use Bind9... I hear the Dnsmasq is faster and easier. I know that TheFu talks about it allot, so he must know a lot more about that than I on that.

What I would do? In the past I did separate machines... Then consolidated my 14 servers into one machine, using a VM host, with VM Server Guests, with a bridged NIC so it had access to the host network. That was around Ubuntu 10.04 LTS(?) That is what got me interested in virtual host systems, and in KVM specifically.

I think TheFu does some of the same, but also uses LXD containers for some of his services. So, he also seems to virtualizes his needed services.

[COLOR=#0000ff]**Yes. I am an old Techie. I can understand the "wanting a challenge" kind of concept. I don't 'require' what I have here, or the ways I still do things. But it is fun, challenging, and fulfilling to me.**[/COLOR]


Precisely.  And I think I will go with a separate physical machine that just runs BIND9 independently.  If I had a "blade server" with that kind of  horsepower, I might combine  the machines virtually. But I currently have a bunch of old towers that are just collecting dust (like my old Windows XP tower) which I think a can repurpose/rebuild.

---

### Post by DuckHook on 2023-07-21
> **mag3lxub said:**
> …I think I will go with a separate physical machine that just runs BIND9 independently…I currently have a bunch of old towers that are just collecting dust (like my old Windows XP tower) which I think a can repurpose/rebuild.

> **DuckHook said:**
> …The whole MS SBS model is broken and bad, especially in the context of Linux. The reason MS touts it is because users have to pay dearly for every server licence in the proprietary world. Therefore, artificial economy dictates that all functions be concentrated into one box. But in the Linux world, server licences are free. You can run as many boxes are you want without paying a dime. Freed from this economic tyranny, the real power of Linux manifests. You should spread your workload among many machines for all sorts of benefits:

Each machine now runs only one function, but runs it well…
You are quickly catching on to the Linux way. ;)

---

### Post by TheFu on 2023-07-21
> **mag3lxub said:**
> Precisely.  And I think I will go with a separate physical machine that just runs BIND9 independently.  If I had a "blade server" with that kind of  horsepower, I might combine  the machines virtually. But I currently have a bunch of old towers that are just collecting dust (like my old Windows XP tower) which I think a can repurpose/rebuild.

These little service/daemons don't really need a physical machine.  Think of it as logical separation only.  Linux Containers are extremely light-weight and useful for things like DHCP, DNS, or any need that doesn't have large compute or data access requirements.  For example, I'd put a busy RDBMS on real hardware, but I run internal DNS systems in linux containers.  I actually use LXD/LXC to run the pihole DNS filtering but it can also provide a very light LAN DNS for local systems.

Linux containers don't require any special hardware. They are 100% software and have been supported since the 2.6.x kernel series ... about 20 yrs now.
While I use a light Ubuntu Server container, there are much, much, lighter options with tiny footprints. Alpine Linux is one, though it is pretty bare and doesn't include many user-land tools most people would expect.  One of my pihole installs is .
```
$ dft
Filesystem             Type           Size  Used Avail Use% Mounted on
lxd/containers/pihole2 zfs             33G  2.4G   31G   8% /

2.4G, which is quite bloated for just DNS.  The 33G total storage is shared by many other Linux Containers.
[CODE]nvme0n1                      disk             465.8G                           
&#9492;&#9472;nvme0n1p3                  part LVM2_member   465G                           
  &#9500;&#9472;vg00-lxd                 lvm  zfs_member     50G                lxd        

```
is the storage view from the host system.  Ah ... LXD really prefers ZFS as the file system.  Generally, I prefer to use LVM2 for storage management, but sometimes it is necessary to give into the wishes of the tool. ;)  They like ZFS, so ZFS it is. ;)

I don't use DHCP except for guests and a few portable devices get DHCP reservations.  I've seen entire networks broken thanks to DHCP.  I set static IPs for all servers and desktops after being burned.  We all have different experiences, so I can understand why using DHCP seems like a good idea.  We did too, until 2000 desktops were kicked off the network and couldn't get back on thanks to a dead DHCP server.   About 20 yrs ago, I was using DHCP at home and ran into a similar issue, so it isn't just large networks, but small ones that can have a really bad day that just isn't necessary and easily avoided.

My main job as an admin is to avoid issues BEFORE they happen.

---

### Post by MAFoElffen on 2023-07-21
Containers and VM's for server services do not take much horsepower if using LXD and KVM. Especially for DNS and DHCP services. Most of the time, those are dormant, waiting to do something. 

Sharing resources in a way that still isolates them logically, is "a new mindset" I learned about a decade ago. Like I said, I went from 14 physical servers, to just one, with the same hardware.

The thing is, you want a challenge to learn new things and ways to do things right? It isn't going to cost your anything to try it... And the time setting it up is not wasted. If you find you need to migrate it to another machine, whether physical or virtual, the config files would already be done, where you just install and migrate the configuration files of the service. (What you had to modify for your environment).

That thing about virtual environments, is that they are flexible and adaptable.

---

### Post by mag3lxub on 2023-07-22
> **MAFoElffen said:**
> Containers and VM's for server services do not take much horsepower if using LXD and KVM. Especially for DNS and DHCP services. Most of the time, those are dormant, waiting to do something. 

Sharing resources in a way that still isolates them logically, is "a new mindset" I learned about a decade ago. Like I said, I went from 14 physical servers, to just one, with the same hardware.

The thing is, [COLOR=#0000ff]***you want a challenge to learn new things and ways to do things right? It isn't going to cost your anything to try it..***[/COLOR]. And the time setting it up is not wasted. If you find you need to migrate it to another machine, whether physical or virtual, the config files would already be done, where you just install and migrate the configuration files of the service. (What you had to modify for your environment).

No, it won't.  And as soon as this current environment is stable, and I learn a bit more about "virtualization" and virtual machines, I'll give it a try. I have a spare Intel Core-i9 CPU chip that I couldn't use in the current builds (not compatible with the Motherboards, as I discovered) :( I just have to find a compatible Motherboard for it. And I can throw a ton of RAM on it.  We'll see.

Thanks.

---

### Post by TheFu on 2023-07-22
Linux virtualization isn't like MSFT.  You don't need that much RAM.  I ran 10 servers in a system with 16GB of RAM and had room to spare.  With Containers, it is even less - about 1/10th the size of a full VM.

Virtualization is one of the things that Linux does better than any other OS ... except, perhaps, MVS.

For the last 20 yrs, every company where I worked, we virtualized everything and it actually took an approved architectural variance from the "board" **_NOT_** to use virtualization.  Of course, there are times when it isn't possible, typically due to external hardware connections, but for stuff most people do at home, virtualizing everything except their gaming system should be the preferred solution.

I've been running my main desktop as a virtual machine since 2008.  The only MS-Windows system I have left, runs inside a VM, when it is needed.

Some example VMs and Containers running here:
[LIST]
[*]Zimbra server ; MS-Exchange replacement with many, many, more capabilities
[*]email gateway 1/2 ; need to keep very complex Zimbra away from the internet.
[*]Blog server
[*]VPN server ; this is for remote access and all wifi devices to access protected subnets.
[*]Mint Desktop; virtualizing a desktop simplifies many things, especially when traveling. If anything bad happens, falling back to the last snapshot erases any issue, immediately. Of course, we still need backups and snapshots ensure those backups aren't corrupted.
[*]static websites + reverse proxy server
[*]nextcloud server - does lots of things, but mainly is an RSS feed consolidation tool
[*]Internal document and photo collection server
[*]pihole1/2 servers
[*]wallabag server (like Read-It-Later for webpages)
[*] mpd music servers
[*] Jellyfin Media Center
[/LIST]
Today, I have multiple subnets, multiple VPNs, an overlay mesh VPN 

If you google "self-hosted", lots of ideas will be shown.  The Sovereign project has Ansible playbooks to setup the most popular self-hosted stuff. [https://github.com/sovereign/sovereign](https://github.com/sovereign/sovereign)   The only tools in that list I'd avoid is tarsnap. There are many better backup tools and techniques.

---

### Post by mag3lxub on 2023-07-23
> **TheFu said:**
> Linux virtualization isn't like MSFT.  You don't need that much RAM.  I ran 10 servers in a system with 16GB of RAM and had room to spare.  With Containers, it is even less - about 1/10th the size of a full VM.

Virtualization is one of the things that Linux does better than any other OS ... except, perhaps, MVS.

For the last 20 yrs, every company where I worked, we virtualized everything and it actually took an approved architectural variance from the "board" **_NOT_** to use virtualization.  Of course, there are times when it isn't possible, typically due to external hardware connections, but for stuff most people do at home, virtualizing everything except their gaming system should be the preferred solution.

I've been running my main desktop as a virtual machine since 2008.  The only MS-Windows system I have left, runs inside a VM, when it is needed.

Some example VMs and Containers running here:
[LIST]
[*]Zimbra server ; MS-Exchange replacement with many, many, more capabilities 
[*]email gateway 1/2 ; need to keep very complex Zimbra away from the internet. 
[*]Blog server 
[*]VPN server ; this is for remote access and all wifi devices to access protected subnets. 
[*]Mint Desktop; virtualizing a desktop simplifies many things, especially when traveling. If anything bad happens, falling back to the last snapshot erases any issue, immediately. Of course, we still need backups and snapshots ensure those backups aren't corrupted. 
[*]static websites + reverse proxy server 
[*]nextcloud server - does lots of things, but mainly is an RSS feed consolidation tool 
[*]Internal document and photo collection server 
[*]pihole1/2 servers 
[*]wallabag server (like Read-It-Later for webpages) 
[*] mpd music servers 
[*] Jellyfin Media Center 
[/LIST]
Today, I have multiple subnets, multiple VPNs, an overlay mesh VPN 

If you google "self-hosted", lots of ideas will be shown.  The Sovereign project has Ansible playbooks to setup the most popular self-hosted stuff. [https://github.com/sovereign/sovereign](https://github.com/sovereign/sovereign)   The only tools in that list I'd avoid is tarsnap. There are many better backup tools and techniques.

Thanks much.  I'll check them out.  Just let me get things stabilized on the Ubuntu domain controller (and the Windows Server 2003 controller decommissioned), and then I can start looking at these options.

---

### Post by mag3lxub on 2023-07-26
> **TheFu said:**
> 

I've been running my main desktop as a virtual machine since 2008.  The only MS-Windows system I have left, runs inside a VM, when it is needed.

If you google "self-hosted", lots of ideas will be shown.  The Sovereign project has Ansible playbooks to setup the most popular self-hosted stuff. [https://github.com/sovereign/sovereign](https://github.com/sovereign/sovereign)   The only tools in that list I'd avoid is tarsnap. There are many better backup tools and techniques.

I'm starting to like LXD a lot more. I've been reading up on it.  When I'm able to buy a new Motherboard that is "Core-i9" compatible, I'll put that box together and build it to host the DHCP and DNS servers as well as, maybe my last and remaining Windows install (if I can relocate it from my old machine).

Question: If you create a Virtual Windows workstation using LXD, are you still required to enter a valid "product code"  as you would if you installed Windows Raw on a separate  box? I mean, my product codes are probably expired now (Windows 7 64bit "Ultimate" Ed.). If, for example, I was ever to replace the motherboard or CPU on my existing desktop box, it would make me re-enter the original product code, which it won't accept now because it's so old.  And when you call Microsoft to get a valid "updated" product code, they're going to try and force you to upgrade.  Not happening. 

And, to complicate things even further. I've been dealing recently with a networking issue wherein my main desktop's NIC is going into "Unauthenticated" status, intermittently.  I lose DNS as a result. Rebooting the box seems to correct it but only until it goes "Unauthenticated" again and fails again. There's no rhyme or reason in re: how often it occurs or when/where, etc. I'll just be browsing/typing away and, all of a sudden, total freeze.  When I open the "Network and Sharing Center), it says my connection is "Unauthenticated."  I wonder if it might have something to do with my Ubuntu DC being on the same subnet as my original Windows Server PDC and causing issues. I've just powered down the Ubuntu Server and we'll see if it still happens after that.

---

### Post by MAFoElffen on 2023-07-26
Which Gen i9? I sort of have an eye for hardware value for the $...

I have both 9-10900 and 9-13900K. First one I have a Gigabyte board for. I have it as a server with 6 SSD's and 7 NVMe drives. 

For the 13th Gen, the second one there, I bought an MSI MPG Z790 Edge Wifi. That one is for my Workstation. I am retiring my old AMD Opteron 6386 SE Bulldozer in a MicroServer Server board and replacing it with that. I am adding an ESP partition and converting the boot loaders from MBR to UEFI, for both Ubuntu and Windows.

---

### Post by DuckHook on 2023-07-26
> **mag3lxub said:**
> I'm starting to like LXD a lot more. I've been reading up on it.
LXD is indeed an awesome platform. If you want to see how I have leveraged it, check out the link in my sig: Sandboxing Apps with LXD
> Question: If you create a Virtual Windows workstation using LXD, are you still required to enter a valid "product code"  as you would if you installed Windows Raw on a separate  box?
You cannot create a Virtual Windows session directly in LXD. It is container technology, not a virtual machine. As conatiner tech, it will run only OSes that use the Linux kernel. You can *manage* a VM through LXD (which is what I do), but you can also do that the traditional and far more popular way through KVM/QEMU or VMWare or VirtualBox or Xen or…

If you install Windows into a VM, you will need to transfer your old Windows product code into the virtualized OS to get full functionality. This is not hard to do, but you will have to websearch the process of removing it from the old OS and transferring into the new. That's also what I did when moving my W10 licence. I don't recall all the steps anymore, but it involved a few commands on the powershell, then noting the transfer product code, then entering into the new OS. Easy to websearch.
> …to complicate things even further. I've been dealing recently with a networking issue wherein my main desktop's NIC is going into "Unauthenticated" status, intermittently.  I lose DNS as a result. Rebooting the box seems to correct it but only until it goes "Unauthenticated" again and fails again. There's no rhyme or reason in re: how often it occurs or when/where, etc. I'll just be browsing/typing away and, all of a sudden, total freeze.  When I open the "Network and Sharing Center), it says my connection is "Unauthenticated."  I wonder if it might have something to do with my Ubuntu DC being on the same subnet as my original Windows Server PDC and causing issues. I've just powered down the Ubuntu Server and we'll see if it still happens after that.
Networking issues are beyond my pay grade, but it was stuff like this that had me finally chucking the whole garbage Windows legacy components altogether and going pure Linux instead. I have no idea what the cause of your issues are. But running a pure NFS/ext4 environment has been a stress&#8209;free problem&#8209;free cakewalk compared to all the gremlins that plagued me when I first started out with Linux years ago while insisting on the Windows CIFS/NTFS paradigm.

I suppose you will learn this in your own way and at your own time.

---

### Post by mag3lxub on 2023-07-26
> **DuckHook said:**
> LXD is indeed an awesome platform. If you want to see how I have leveraged it, check out the link in my sig: Sandboxing Apps with LXD

You cannot create a Virtual Windows session directly in LXD. It is container technology, not a virtual machine. As conatiner tech, it will run only OSes that use the Linux kernel. You can *manage* a VM through LXD (which is what I do), but you can also do that the traditional and far more popular way through KVM/QEMU or VMWare or VirtualBox or Xen or…  [COLOR=#0000ff]***I'll look into KVM as well. ***[/COLOR] 

If you install Windows into a VM, you will need to transfer your old Windows product code into the virtualized OS to get full functionality. This is not hard to do, but you will have to websearch the process of removing it from the old OS and transferring into the new. That's also what I did when moving my W10 licence. I don't recall all the steps anymore, but it involved a few commands on the powershell, then noting the transfer product code, then entering into the new OS. Easy to websearch.  [COLOR=#0000ff]***I'll have to look into how to "deactivate" a Windows product code, and whether or not I can do that going back to Windows 7.   Obviously, re-installing using the original product code will trigger the "Call us to validate" process, as they think it's being used multiple times. When you call, they tell you it can't be used anymore and you must upgrade. Not gonna happen. ***[/COLOR]  

Networking issues are beyond my pay grade, but it was stuff like this that had me finally chucking the whole garbage Windows legacy components altogether and going pure Linux instead. I have no idea what the cause of your issues are. But running a pure NFS/ext4 environment has been a stress&#8209;free problem&#8209;free cakewalk compared to all the gremlins that plagued me when I first started out with Linux years ago while insisting on the Windows CIFS/NTFS paradigm.

I suppose you will learn this in your own way and at your own time.

I guess I will.     As far as my current status is concerned, I powered down the Ubuntu Server this morning, and the error hasn't happened again in almost 10 hours. That might have been the trouble... having both DCs on the same subnet without creating the forest and making one of the servers "Primary."   I may need to isolate the Ubuntu boxes separately (i.e. separate subnets) while testing with them.

---

### Post by mag3lxub on 2023-07-26
> **MAFoElffen said:**
> Which Gen i9? I sort of have an eye for hardware value for the $... [COLOR=#0000ff]***11th Gen (I9-11900K)  LGA1200 socket***[/COLOR]

For the 13th Gen, the second one there, I bought an MSI MPG Z790 Edge Wifi. That one is for my Workstation. I am retiring my old AMD Opteron 6386 SE Bulldozer in a MicroServer Server board and replacing it with that. I am adding an ESP partition and converting the boot loaders from MBR to UEFI, for both Ubuntu and Windows.

I was looking at a GIGABYTE Z590 UD AC (LGA 1200/ Intel Z590) board,  but it's a bit expensive, right now.   We'll see.

---

### Post by mag3lxub on 2023-07-28
Quick Update:  I'm ready to declare the NIC/Networking issue I was experiencing "resolved."  Once I powered off the Ubuntu Server running as the DC, everything came back to normal.  I guess both DCs could not be on the same subnet without creating a forest/hierarchical structure for them (i.e. making one "Primary" and the other "backup").  

I could create a different subnet for the Ubuntu side, until I'm ready to merge. And, in fact, I have a spare Router I can use as the "default gateway" for that different subnet.  But I only have one ISP source (i.e. one cable modem). And one would think that I could split it with a NIC cable Y-Splitter.  But my understanding from the companies that make those splitters is that they only accept throughput from one side at a time, I don't know if that's true or not, but more than one company has said so. And I wouldn't want to deal with having to re-configure both routers to accept only traffic from their respective subnets.   

I guess I'll have to keep one or the other DC Powered off while I test and until I'm ready to decommission the Windows PDC and promote the Ubuntu server as PDC. We'll see.

---


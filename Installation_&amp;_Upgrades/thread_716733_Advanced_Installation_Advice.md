---
title: "Advanced Installation Advice"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by Ingla on 2008-03-06
Hello.

This is a request for advice, based on experience if possible, regarding installation of Ubuntu with various directories on separate partitions:

_Introduction to Problem_: *Please read this to get an idea of exactly what I need to know*. I use the computer for business and my setup can get kind of elaborate. I cannot afford to be down. On Windows, I have two identical hard drives which are kept synched but only one of which is in the machine at a time - usually. Data is stored on a separate partition.

While I can rebuild the setup from scratch, I save time in the event of an emergency, by formatting the C drive and ghosting it from the remaining hard drive - or - in the event of a hard drive crash, by ghosting everything onto a new hard disk.

The only time I really need to do a lot of rebuilding is when there is a version change (98 -XP, etc.).

Since I prefer to use Linux - specifically Ubuntu - I have to find the very fastest and easiest and most reliable way to deal with version changes. Obviously, these are much more frequent than Windows version changes. This poses a problem for the business user as I can't be completely rebuilding the system every 6 months or so.

On my most recent installation of Ubuntu (7.04 Feisty), I put the home directory on its own partition, I have not yet tried to install a later version while making sure the home partition isn't overwritten, but sooner or later I'll have to. Also, I'm not sure a separate home partition is enough.

(*I use Automatix after an install to put in a lot of things at once. I've been advised that a clean install of the OS is safer than attempting an upgrade after using all kinds of scripts, etc.*) Anyone disagree?
[U]
The main problems[/U] I'll face are keeping confugurations for Thunderbird, Firefox, ftp server, Linux to Linux network (nfs), wine and/or VMWare

_So, the questions _(please comment on any or all of these as your experience allows):

1._Partitions:_ some people install Linux with separate partions for home, var, and usr. 

	a.That sounds good on the face of it, but it occurs to me that it may not always work - or may even break something, if there are version changes in software with which the old configuration files are incompatible. So, maybe Thunderbird 1.5 profiles, and the like, will only mess up Thunderbird 2, for example. 

	b.Are these partitions sufficient or do some of the programs mentioned throw things in other directories.

Any experience on this??

2. _Thunderbird:_ my Thunderbird setup, not counting extensions and themes, is kind of complex. I have lots of e-mail accounts, lots of folders and lots of message rules. It takes quite a while to redo this. Does anyone know what files or folders I would need to back up ALL of these configurations? (There is an extension for exporting all this and importing to a new installation of Thunderbird, but I found it worked one time and messed up everything the next time I tried it.)

3. _Wine:_ will it work to make a backup of, say, .wine, then install wine on the new version and replace the .wine directory with the one I've saved? Would I need to reinstall programs under wine or would replacing the whole folder keep them there as they were?

4. _Networking and ftp server:_ I hope the devs make this just work some day as they have for Windows networks. Feisty just connects with no problem to Windows machines with a shared folder. Linux to Linux is still a major pain. For now, is there anyway to carry all this forward to a new installation? I don't even know where all the files are located or what to back up.

5. _Home Partition:_ I assume that some critical directories will be overwritten by the automatic installation of software - EVEN if I tell the install program not to overwrite. For example, .thunderird would probably be replaced during a new installation. Presumably, I would need to rename it and then switch back after installing. Is this correct?

6. _Any other sage advice_ would be appreciated.

Thanks!

---

### Post by bingoUV on 2008-03-06
1. Partitions : Old configuration files are usually incompatible with new version of the software. This is no different in the case of multiple partitions than when everything is in the same partition. 

     When the new version is installed, the installer upgrades system wide configuration files (generally in /etc). When you first run the application as a particular user, say ingla, the application upgrades the user specific configuration files so that now it is compatible with the current version.


5. As I said in the point above, installation generally does not tinker with user specific configuration. So upgrading thunderbird from 1.5 to 2.0 will not touch $HOME/<username>/.thunderbird but it will upgrade /etc/thunderbird (or wherever system wide configuration is stored). Running thunderbird will cause upgrade of configuration files in home directory.


6. Since you do not want to upgrade every 6 months or so, use a long time support distribution (some Ubuntu versions are LTS). If redhat like stuff is fine with you, you could use CentOS. If you can pay for support, try Suse or Redhat enterprise. All these are supported for a long time period, at least 5 years. Generally you can apply only critical security updates and keep the system generally stable.

---

### Post by Ingla on 2008-03-06
Thanks for the reply.

As many of the personal settings in, say, Thunderbird are in files I can't easily read, I don't know where the accounts, folders and message rules are stored. If they're in ~/.thunderbird, I shouldn't have a problem. But, if they're somewhere else I would need to start from scratch. 

I don't really mind reinstalling themes or extensions ... just takes a few mintues. But the above are a lot of work.

[I][U]Any idea where those things are?
[/U][/I]
Note: As for LTS versions, your're right. I have Dapper on another machine. Only thing is, Feisty is sooo much better ... makes a breeze out of some things I really had to work at in Dapper. I don't usually take every new version, but upgrade at some point because of the improvements ... in any case a lot more often than I would on Windows.

---

### Post by zvacet on 2008-03-07
I don´t konw about Thunderbird but main reason to have separate home partition is to save all your settings and files(if you have them).Backing up just in case is good idea**.During upgrade do not format home partition.**If you do that it will erase everything you have on it.I´&#7743; doing regular upgrades and never had any problem.I allways do upgrade with alternate CD just in case that something goes wrong I have CD for fresh install.Never need it for that purpose.You can extract your addresses and bookmarks from Thunderbird and sent to yourself by mail if you are afraid they can be ruined.

---


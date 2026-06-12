---
title: "Selective automatic updating"
date: 2012-04-25
forum: Installation &amp; Upgrades
---

### Post by houseworkshy on 2012-04-25
I've searched before posting this and found one very old thread which  suggested enableing backports, pulling in one package and then  disableing backports again.  I'd like something simpler as I'd prefer  the package to be updated daily and without fuss.  

Specifically it's the  anti virus engine and its database; clamav freshclam and the various  bits that go with them.  Is there a way of doing this other than  manually adding specific extra repositories, which I've done in the  past,  or enableing the whole backports one?  Something like "mark only  this from this repository for regular updates, not the rest"  Occasionally I'm also interested in the devolpment versions of various  things but never the entire backports repository.
  
I have a  second reason for asking about this; I hear that later ( I'm still on  10.04 lts ) versions of Ubuntu don't ask for passwords before updateing,  sometimes there are issues about various packages or package hardware  combos, especially when freshly released ( often driver stuff) or near the end of support ( updates broke 8.04 a few times near the end ).  In  the past I've simply unchecked what I know is currently causeing  problem in the update manager.  So it would also be nice to know how to  exclude this or that and it's dependancies from upgrading.

To  summerise is there a way of easily marking "excludes" and "includes"  when one only wants a few packages from backports or wishes to avoid  specific updates which may be troublesome. Once marked they'd stay that  way untill one said otherwise so the update manager, or apt-get  update/upgrade, could just do it's thing.  

A few family and friends with serious aversions to anything geeklike are on Ubuntu and because I recomended it in the first place ....

---

### Post by strask on 2012-04-25
> **houseworkshy said:**
> I have a  second reason for asking about this; I hear that later ( I'm still on  10.04 lts ) versions of Ubuntu don't ask for passwords before updateing,
I'm running the latest and greatest 12.04 right now and it has consistently asked for my password before installing updates. So I don't think you need to worry about that part.

Maybe I misunderstand something here (I'm new to ubuntu, and to the way it does package management) but I feel like it should only pull updates for packages you have installed, so if you only installed one package from backports that would get updated and the rest of backports would be ignored, right? What am I missing?

---

### Post by houseworkshy on 2012-04-25
You're right only the installed packages are updated, however sometimes something which worked ok when installed has an update which can break it.  I'd like to be able to exclude certain things from update because they work now but I've read a lot of "help updates broke my installation".  I've seen this happen quite a few times, grub, nvidia drivers ( been reading a few of those this time round already, not much ubuntu can do about that as they are proprietry ), keyboard mapping, all sorts of stuff over the years.
 
It's not that common, ubuntu is a beauty when it has run in a bit, but I've seen it often enough to wish to prevent it.  I'd also like to make it easier as some familly members, who I don't live with, ring me up to help when things go wrong.  The last of the 8.04 ones was too much for me, white screen of death,  and after a couple of days banging my head against it,  had to format and reinstall. The affected machine owners, use applications a lot, hate the under the bonnet stuff, can't afford downtime  so turned off updates altogether as they didn't trust them anymore.  I don't like the idea of not updating in general so it'd be nice if I could exclude known problem updates from the rest untill they are fixed.

The backports include more developmental versions of things which are more stable in the standard repositories, so enableing backports for the sake of, say the latest antivirus scanner, would also mean the update manager would look for updates to any package on the system which has a developmental version in backports, not just the virus scanner, every app on the system and the system itself.  I'd like to say, "backports for this application and it's dependancies but nothing else backports", and "all of everything in the main repositories except whatever seems to have a current problem that I wish to avoid for a while."

Glad to hear that you are being asked for a password by update manager, that would suggest a rethink.  I'd got the info from this thread which was actually 11.10 
[http://ubuntuforums.org/showthread.php?t=1811202](http://ubuntuforums.org/showthread.php?t=1811202)
I've stuck with the 10.04 LTS version as I've not really had the time this cycle for the intermediaries.  Took a beta 12.04lts for a live spin to look at it but hadn't tried the update manager.  Good news for me a definate inducement to go with the next lts.  Thanks for the info.

---

### Post by RichardCain on 2012-04-26
> **houseworkshy said:**
> I'd like to say, "backports for this application and it's dependancies but nothing else backports"
As far as I know, this is not possible; backports is an <i>all or nothing</i> kind of selection (although I'd be interested to hear otherwise.

> **houseworkshy said:**
> "all of everything in the main repositories except whatever seems to have a current problem that I wish to avoid for a while."
Again, the system is specifically designed to simply check what new information a repository has, cross-reference that with the list of packages installed, and download everything that matches.

It's been a while since I actually used the update manager (I normally use a script from a terminal), but is there not a way to deselect certain individual updates?  I know Mint has this.  This would seem to be the only way around this.  Hard work I know, especially for *family and friends with serious aversions to anything geeklike*, as you would have to regularly have to check for anything that had known problems.

Having said that, I have never found the need for updating virus info via backports; it's really not that much of an issue.  Anti-virus programs on Linux only guard against inadvertent transmission of Windows viruses after all.

---


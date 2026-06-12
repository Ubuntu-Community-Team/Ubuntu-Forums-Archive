---
title: "Power failure during upgrading to 12.04 screwed up"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by jaj540 on 2012-04-26
I was upgrading my Ubuntu 110.10 to 12.04 .after downloading packages it had started applying changes.... and then the power fsilure occured..Now i cannot start my ubuntu...after selecting ubuntu from grub, a black screen comes and nothing else.not even the logo of ubuntu .. :( How I can continue my upgrading?... I took in recover mode and tried to repair broken packages..then there came a message like some of your filesysten has errors....pls help me...:(

---

### Post by jadtech on 2012-04-26
at this point unless you can get it to boot your not gonna get to finish or restart the upgrade, if there is a way to get to a term I will bet there is away to get to recovery  ..

not sure if there is a solution but while waiting  loading a live disk and trying to get any files you might want to rescue from your home or root might be  a good Idea ..

---

### Post by LinuxFan999 on 2012-04-26
The only way to upgrade if your current system can't boot is to do a clean installation of Ubuntu 12.04 (a clean install is the best way to upgrade Ubuntu).

---

### Post by Bucky Ball on 2012-04-26
> **LinuxFan999 said:**
>  (a clean install is the best way to upgrade Ubuntu).

Once more; why?

---

### Post by oldfred on 2012-04-27
Can you boot into a command line from recovery mode? if so you can run several repairs. If you cannot get to a command line, then you may be able to chroot into your install and run repairs.

Examples of chroot. You may not may not need to reinstall grub2.
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

Then once chrooted or at command line. # are comments do not copy or type.

#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

### Post by jaj540 on 2012-04-27
@oldfred   : I can access commandline from recovery mode
and when I tried apt-get autoclean it comes the following response
"
W:Not Using locking for read only lock file /var cache/apt/archives/lock
W:Nott using locking for read only lock file /var/lib/dpkg/lock
E:Unable to write to /var/cache/apt/
E:The package lists or status file could not be parsed or opened

---

### Post by jaj540 on 2012-04-27
> **jadtech said:**
> at this point unless you can get it to boot your not gonna get to finish or restart the upgrade, if there is a way to get to a term I will bet there is away to get to recovery  ..

not sure if there is a solution but while waiting  loading a live disk and trying to get any files you might want to rescue from your home or root might be  a good Idea ..

I am getting into command line through recovery mode

---

### Post by oldfred on 2012-04-27
When you boot is it going into read only (ro) mode? You may be able to remount as read/write or it has some issue with system and you may need fsck.

#From liveCD so everything is unmounted,swap off if necessary, change example shown with sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by mouton on 2012-09-01
Hi Oldfred et al,

I had a similar problem - running Ubuntu in a virtual box, doing a dist-upgrade and the Windows host decided to crash and reboot.
Running the commands you offered is either met with silence (good ¦¬]  ) or with 

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  libc-dev-bin: Depends: libc6 (< 2.12) but 2.15-0ubuntu10 is to be installed
  libc6-dev: Depends: libc6 (= 2.11.1-0ubuntu7.10) but 2.15-0ubuntu10 is to be installed
  libnih1: Depends: libc6 (< 2.12) but 2.15-0ubuntu10 is to be installed
  python-louis: Depends: python2.7 but it is not going to be installed
                Depends: python (>= 2.7.1-0ubuntu2) but 2.6.5-0ubuntu1 is to be installed
                Depends: liblouis2 (>= 2.3.0-3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


I tried that of course, with -f. Same result. I very hopefully completely removed one of the offending packages, and tried to install it afresh, but then another unhappy package takes it's place.
I *could* do a clean install on the VM, but there are months of little tweaks in the environment I'd hate to have to re-work-out.

Is there any way to save the botched install? Thank you very much!
Ulrich

---

### Post by oldfred on 2012-09-01
I do not understand why you are getting the old versions on those applications.

My libc6 shows it is the 2.15. And python is 2.7.3. What if you just try to install each of the files like:

sudo apt-get install python

What version does it install or says is installed?

---

### Post by mouton on 2012-09-02
Thank you, oldfred!
Alas, whether "-f" or not, attempting to install "sudo apt-get install python" plays a similar game:

> Reading package lists...
Building dependency tree...
Reading state information...
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  command-not-found: Depends: python (< 2.7) but 2.7.3-0ubuntu2 is to be installed
  computer-janitor: Depends: python (< 2.7) but 2.7.3-0ubuntu2 is to be installed
  computer-janitor-gtk: Depends: python (< 2.7) but 2.7.3-0ubuntu2 is to be installed
  gdebi: Depends: python (< 2.7) but 2.7.3-0ubuntu2 is to be installed
  gdebi-core: Depends: python (< 2.7) but 2.7.3-0ubuntu2 is to be installed
  jockey-common: Depends: python (< 2.7) but 2.7.3-0ubuntu2 is to be installed

it continues in that vein for 70-odd lines to
> 
  python-zope.interface: Depends: python (< 2.7) but 2.7.3-0ubuntu2 is to be installed
  screen-resolution-extra: Depends: python (< 2.7) but 2.7.3-0ubuntu2 is to be installed
  software-properties-gtk: Depends: python (< 2.7) but 2.7.3-0ubuntu2 is to be installed
  ufw: Depends: python (< 2.7) but 2.7.3-0ubuntu2 is to be installed
  update-manager: Depends: python (< 2.7) but 2.7.3-0ubuntu2 is to be installed
  update-manager-core: Depends: python (< 2.7) but 2.7.3-0ubuntu2 is to be installed


*sigh*
Any hope?

Thanks a lot!

---

### Post by oldfred on 2012-09-02
It is like the update is out of sync. It is seeing old versions, so it will not let you update to new version. 
Someone in the last week did post something about clearing a cache. Not sure if same issue or not, but I did not save details.
Is your sources list consistently one version, not half way changed?

cat /etc/apt/sources.list

---


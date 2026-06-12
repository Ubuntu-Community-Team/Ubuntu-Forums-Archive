---
title: "kernel update and ecryptfs problem with ssh"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by Griffino on 2010-08-22
Hello, I've started running Linux 2.6.32-24-generic-pae (#41) on several machines with Ubuntu 10.04.  All of these machines use encrypted home directories using ecryptfs.  I have chosen the option (encrypted home directories) when I installed Ubuntu on these machines, and it seemed to work well.  After a local login or a remote login (using ssh with the RSA key authentication with the "authorized_keys" file configured to be located outside my encrypted home directory), the home directory is mounted automatically, and after I logout it is unmounted.

However, after a recent kernel update, maybe a day or two ago, I am observing a slightly different behavior than before.  When the machine is booted fresh and I login using ssh with the public RSA key, my home directory is not mounted automatically.  This behavior is different from the behavior before the kernel update.  However, if I then run the command "ecryptfs-mount-private" manually, which requires me to type the password, or if I login to that machine by typing the password, then my home directory is mounted automatically.  Furthermore, if I subsequently logout of my account (which unmounts my encrypted home directory -- I checked), and then I ssh to that host again with the public RSA key, then the home directory is now automatically mounted!

So, it appears, as far as I can see, that the machine somehow requires me to type the password at least once after a clean-boot in order for the automatic mounting of my encrypted home directory to work.

Of course, I haven't tested all possible scenarios, but what I have done so far indicates something like this might be going on.

I really don't see the point of this behavior.  Maybe this is a new bug introduced by the kernel update?  Or maybe after the kernel update, pamd and ecryptfs have some catching up to do?

If any one can shed light on how I can get the original behavior back -- i.e. pamd, ecryptfs and ssh working happily together without me having to type the password (and without having to wait for the X authorization to time out as the home folder is not ready), that would be great.

---

### Post by MartinSixta on 2010-09-04
I'm having the same problem (latest x64 virtual kernel). But I have to run  "ecryptfs-mount-private" manually every time. Any news?

---

### Post by rsay on 2010-09-09
I have tried the following kernels without success, suggesting to me that this is not a recent kernel update problem:
2.6.32-24-generic
2.6.32-23-generic
2.6.32-22-generic
2.6.32-21-generic

Somehow, the encryption keys have to get loaded into the kernel keyring before public key authentication can unlock the home directory.

As you described, my encrypted home directories are not mounted with ssh public key authentication unless I log in locally from the laptop first. 

I keep my ssh authorized_keys in an unencrypted directory. My laptop wakes up at 1am every day for backup. My local backup server pulls the unencrypted data from the home folders with rdiff-backup, which runs over ssh unattended. I need this behavior to work consistently or I will end up with a real backup one day and then Access-Your-Private-Data.desktop and README.txt the next day, which will ruin the integrity of my incremental backup chain and significantly increase my storage requirements due to the illusory changes in the data from day to day.

Is there some sort of configuration file that can be changed to allow ssh w public key authentication to load a users enryption keys into the kernel keyring?

---

### Post by rsay on 2010-09-09
For now, I have decided on a compromise, since I don't know how to push my keys to the kernel keyring from a script.

I moved my ssh authorized keys back into the encrypted home directories and disabled password authentication for ssh. :eek:

The result of these changes is that my backup process will only be able to backup the data for users who have logged in since a reboot. Since these are the only users who would realistically have new data, I think I am pretty safe from data loss. The only way you could lose data would be to log in, write the great american novel, reboot and lose/damage the computer before the next time you logged in and let the computer run overnight without rebooting or shutting down.

We usually leave the laptop on 24/7 with suspend after 1 hr and suspend with lid close. The laptop wakes up at 1am daily to make itself available for a backup pull. (I use a pull because I don't want the laptop to automatically attempt to push clear data, when it is on another network.) Twice monthly, the computer leaves the house for a business trip.

I also lose ssh access into the laptop, if I haven't logged in since a reboot, which would hardly ever occur and would be a minor hassle if it did. I disabled the ssh password login so my backup would fail instead of hanging on a request for manual password entry, if I ran into an unencryptable home folder. By encrypting the authorized_keys, I can never accidentally backup Access.Your.Private.Data.desktop which preserves the integrity of my incremental backup chain.:)

---

### Post by JonTheNiceGuy on 2010-10-04
It's good to see it's not just me with this issue (although, a search around Launchpad would suggest I am!)

Did you file a bug for this? If so, do you still have the ticket number? I'd like to see what, if anything, was the response.

Like with you, it's not particularly damaging for it not to be working, but it's frustrating, especially as I use Byobu on my server in question, and as such, when I log in, I don't get my magical byobu stuff starting up ;)

All the best,

Jon "The Nice Guy" Spriggs

---

### Post by rsay on 2010-10-06
I have not filed a bug. I don't have a good enough understanding of the security implications to know what the most desirable functionality is.

---

### Post by JonTheNiceGuy on 2010-10-06
Likewise, I don't know the appropriate security behaviour here, but I've filed a bug to see what discussion happens as a result.

[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/655726](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/655726)

---

### Post by FunGuyDRW on 2011-08-12
So about a year since the last person had this ecryptfs problem and now I'm having the same issue -- or a similar one. Beginning about a month ago upon booting Ubuntu I got an error to the effect of "Can't write to the drive: permission denied". I figured out that this is because ecryptfs isn't decrypting my home directory. But I have no idea how to fix that manually at login, even after reading the ecryptfs-utils man page. (It's mostly gibberish to me.)


I'm using Ubuntu because I don't know a lot about computers. I use LTS 10.04 because I don't want to have to change stuff and risk problems. I wish I hadn't done the automatic kernel update or whatever caused this problem.

In this case I was able to at least start an OS because I had a live cd of Puppy Linux. But Puppy doesn't run programs I absolutely need to get work done. So it's been several weeks of googling through Puppy and I still haven't been able to get back into my files!

---

### Post by DrPotoroo on 2011-09-20
Did your problem follow a password change? Try running ecryptfs-mount-private and using your current password. If that doesn't work, try your previous password. If that doesn't work, did you write down your decryption passphrase somewhere when the encrypted dir was first set up?

---


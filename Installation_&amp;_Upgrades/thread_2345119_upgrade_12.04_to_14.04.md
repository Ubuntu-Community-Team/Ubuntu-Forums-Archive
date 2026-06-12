---
title: "upgrade 12.04 to 14.04"
date: 2016-11-30
forum: Installation &amp; Upgrades
---

### Post by brumman on 2016-11-30
My Ubuntu 12.04 LTS will soon be unsupported so I want to upgrade to the latest LTS version but I know this should be done in stages, so via 14.04 first.
My concern is how and what to backup and what can be ignored before upgrading? 
On my ubuntu system as well as the Linux file system (ext4) I also have a large partition for DATA which is NTFS so that I can also access it from my windows installation on a separate drive. Can I back all this up (using Deja Dup or similar) without problems?   
I have an external drive which is formatted as NTFS and contains a windows7 back up - is it possible to shrink and partition this drive so that the Ubuntu backup could also be stored there?

---

### Post by TheFu on 2016-12-01
What needs to be backed up is completely dependent on what you've installed and how you use the system. We cannot answer that for you.  If you list the applications and servers that are used, perhaps someone could help? I dunno.

Before any upgrade, a backup is mandatory. Actually, I consider daily backups mandatory, just so I can sleep.  If it isn't sufficient to put back what you had before, then it isn't enough of a backup.  If you haven't tested the backup+restore at least 3 times, it isn't a backup either.  How will you know what is missing or failing or learn the restore steps without practice?

As to the tool to use, there are many. It is a personal decision.  Before picking a tool, look for "{tool} failed" on the internet and in these forums so you know some common failures.  Nothing can replace practice. There are many tiny details that will be missed otherwise.  If you don't have time to figure all this out, go purchase new storage and just swap the disks.

Some Linux backup tools **can** use NTFS storage, but many cannot. This is because NTFS doesn't use the same permissions model as Linux/Unix does, so user/group/permissions and ACLs are lost.  Can you shrink an NTFS partition?  Perhaps. Depends on how it was created. MSFT has made hybrid file systems which are not compatible with Linux tools at all.  Their official conversion process is to backup the data, reformat using the desired file system, and restore.  That doesn't change the partition size, so that will need to happen next.

Get thee backup religion. You've been lucky so far, but that luck will run out. That tends to happen in the middle of large, heavy use, like installing a new OS.

---

### Post by brumman on 2016-12-07
Thanks TheFu,
I thought that apart from data folders only the home folder needs to be backed up since all applications can be reinstalled if necessary. i will follow your advice and research backup failures, but if something is missed during backup won't restoring mean permanent loss?
 I'm not sure what you mean by "purchase new storage and just swap the disks". Do you mean clone to a new disk and then upgrade the original, or a fresh install (say 16.04) on a new disk and painstakingly installing my current applications and data. 
You are right about the importance of backups - I have that external drive with a Win7 backup because my Windows system crashed but I was able to copy all the data and installed programs info using my Linux disk.

---

### Post by TheFu on 2016-12-07
On Linux, as long as the files "appear" to be in the same place after a restore, that is all that is needed for everything except the grub boot stuff.  Fixing the boot stuff is relatively easy too - grub-install and update-grub.  The data, programs, settings don't have to be on the same partition or even on the same physical machine.

If you are a typical desktop user, then all data will be stored in your HOME.  But why not make the restore easier by capturing a list of all the packages installed and any settings for the system too?  Those are both tiny. 

Clone? No.  The point of buying new storage is to test your restore process on bare metal. Backups without a full, new-disk, restore, test isn't a backup, it is just hope that a backup was sufficient.

Backup data is different types.
* cannot lose ever (wedding photos, password manager DB, bank/credit card accounts, passport data, immunization records)
* would not want to lose (financial data , old bank statements, kids photos, media collection)
* would be a hassle to recreate (system settings, applications, resumes, diaries, journals, new financial docs, installed programs)
If your backup method addresses each of these in a way you can live with, then you've won, provided the restore actually works.  However, some of the least important items are also very easy to retain, backup, restore, why not keep them?

For example, with a list of the currently install programs on my systems, I can feed that into the restore process and not have to manually load those programs again.  This is all thanks to using Canonical repos and trusted PPAs to load software.  Coming from Windows, the closest thing to this is Ninite, but with 35,000 program packages in the Linux packaging system, not 100. Plus Linux package managers handle dependencies.

Anyway, at a minimum, get /home, /etc, and the output from **dpkg --get-selections**.  That probably isn't enough, but it is a start.  I also clean up temporary files that I don't want and exclude cache directories everywhere, especially in HOME.  To make restores easier, I capture the current hardware, current RAID setup, LVM info, disk partitions, file system data, networking info, in ways that can be easily used to make new hardware have similar settings.  If I have to replace the primary disk in a system, it would be nice if the partition layout were exactly the same as I had previously. Right?  Since I have multiple systems, I don't remember the details and need some solid, accurate, help.  

Versioned backups aren't practical for all data.  Large media files that don't change often just need a copy.  Data that is relatively small, can be helped by having versions, daily, 60-120 days worth.  Heard about all those encrypt-disk viruses that are going around?  I don't care.  The encrypted files would be backed up and I'd see it (huge changes and long times), so restoring the system from the night before the encryption happened would be the solution.

I get a daily email report about backups ...```

=== Time for Backups to fe-email === 
StartTime 1481097005.00 (Wed Dec  7 02:50:05 2016)
EndTime 1481097011.67 (Wed Dec  7 02:50:11 2016)
ElapsedTime 6.67 (6.67 seconds)
TotalDestinationSizeChange 1163 (1.14 KB)


=== Time for Backups to lubuntu === 
StartTime 1481091307.00 (Wed Dec  7 01:15:07 2016)
EndTime 1481091577.94 (Wed Dec  7 01:19:37 2016)
ElapsedTime 270.94 (4 minutes 30.94 seconds)
TotalDestinationSizeChange 12009081 (11.5 MB)


=== Time for Backups to hadar === 
StartTime 1481092514.00 (Wed Dec  7 01:35:14 2016)
EndTime 1481092523.41 (Wed Dec  7 01:35:23 2016)
ElapsedTime 9.41 (9.41 seconds)
TotalDestinationSizeChange 21402 (20.9 KB)
```
that's from 3 systems of about 15-20. I'm trying to consolidate now. Was 30 last year. ;)  Anyway, you can see that these backups are relatively quick.  Once in a while, a backup will fail. Because they happen daily, it isn't the end of the world.  Usually the issue is because a Windows share isn't available, so a reboot of Windows fixes it. 

Anyway, if you search these forums, you'll find lots of backup info and techniques from lots of smart people. There are some backup scripts in here too that can be a starting point.

For me, if the restore takes over 30-45 min, then it is a failure.  Blowing away a system isn't a major ordeal like with Windows.  In 30 minutes with about 10 minutes of my hands-on time, it can be back.

---

### Post by brumman on 2016-12-10
@ TheFu
 I really appreciate your advice and I can see I shall have to do a lot of research on backup techniques - but when finished I hope that the upgrade from Canonical is still available!
Incidentally which backup tool do you usually use?
Don't want to appear dumb but I still have a question about new 'bare metal' storage. Would I store the backup on say an external disk and then test restore to a new formatted and partitioned disk?
BTW the output from **dpkg --get-selections** only showed *m - z*, nothing for *a - m* section.  Is this the list you feed into the restore process and how exactly? 
Thanks again.

---

### Post by TheFu on 2016-12-10
I've written elsewhere about my backups. Search the forums. I use rdiff-backup, but that isn't necessarily the best tool for everyone.  I do NOT backup everything, so just restoring the backup alone is NOT sufficient in my method. I don't do image-based backups on Linux either. 

"Bare metal" storage means exactly as it would come from the factory, new.  If your HDD fails, isn't that what you'd use to restore? Everything involved in the restore needs to be practiced, a few times.

When posting issues with commands, 
a) post the exact command used, including the prompt.
b) include the output. If is it really long, only include the beginning, relevant parts and the end. 
c) Always, always, use "code tags" when posting shell output. Things line up that way.

```
$ dpkg --get-selections |more
a11y-profile-manager-indicator                  install
accountsservice                                 install
acl                                             install
acpi                                            install
acpi-support                                    install
acpid                                           install
adduser                                         install
adwaita-icon-theme                              install
alarm-clock-applet                              install
alsa-base                                       install
alsa-utils                                      install
alsamixergui                                    install
anacron                                         install
app-install-data                                install
apparmor                                        install
apport                                          install
apport-gtk                                      install
apport-symptoms                                 install
apt                                             install
apt-transport-https                             install
apt-utils                                       install
aptdaemon                                       install
aptdaemon-data                                  install
aptitude                                        install
aptitude-common                                 install
apturl                                          install
apturl-common                                   install
aspell                                          install
aspell-en                                       install
 ....
youtube-dl                                      install
zenity                                          install
zenity-common                                   install
zenmap                                          install
zip                                             install
zlib1g:amd64                                    install
zlib1g-dev:amd64                                install

```
Works here. 16.04.
If you google that command, there will be the command to restore the selections using "*--set-selections*" as an option.  Test both of these.  There might be newer methods that also work to capture and restore the list of packages. You'll want to redirect the output into a file. Basic Unix stuff.

---


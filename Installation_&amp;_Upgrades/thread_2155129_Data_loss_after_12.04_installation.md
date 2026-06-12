---
title: "Data loss after 12.04 installation"
date: 2013-06-17
forum: Installation &amp; Upgrades
---

### Post by lablouw on 2013-06-17
I'm not a great expert in Ubuntu but here's my predicament: A few weeks ago my old version of Ubuntu (can't remember which version) with encrypted home folder informed me that it was officially no longer supported and I should upgrade. I started the process which failed half way (stalled indefinitely). After resetting all I could get was a blinking mouse cursor. So I downloaded 12.04 LTS, and installed from CD. When prompted I chose the option that stated something along the lines of "Install 12.04 over previous version of Ubuntu" and NOT "Wipe the system and do a fresh installation". After installation and reboot my home directory was that of a fresh install! All my documents and tons of code gone! I am currently running TestDisk from my windows partition but it's not looking promising.

My ubuntu partition was not one I frequented as of late and all I know is my password. Thankfully I still have the latest compiled jar files of my java projects which as a last resort I could decompile, fix up and go back to much older backups to re-insert comments (quite complicated code). If I could just have my working projects direcory back (~/home/NetbeansProjects) I would be happy.

Can anyone please help?

---

### Post by darkod on 2013-06-17
Unfortunately, the "install over previous version" is almost the same as "wipe the disk" when you have only ubuntu. The difference is if you have another OS, the wipe option will wipe all, and the install over will only wipe your old ubuntu and install over it.

First see what testdisk comes up with. It's very good recovering deleted partitions.

As an idea for the future, you might think about having separate /home partition, and/or another data partition where you keep all your important data, and when you want to move to a new release you simply do a clean install reusing the same /home partition and all data partitions. That keeps your personal data safe from the clean install. You might need to tweak few options, but in general that's not too difficult compared to the safety you get doing clean installs compared to upgrades which often give issues.
You can even export the list of packages/programs on the old install, and import it into the new one which should install all newer versions if available.

---

### Post by varunendra on 2013-06-17
> **lablouw said:**
> When prompted I chose the option that stated something along the lines of "Install 12.04 over previous version of Ubuntu" and NOT "Wipe the system and do a fresh installation".

Unfortunately, the process of installing over an existing installation involves 'deletion' of existing system files/folders on the target partition even if you don't choose to format it *(as is confirmed when you choose "something else" for manual partitioning and choose not to format the existing partition)*.

This is done to avoid conflicts with existing setup/configuration.

Sorry to be the bearer of the bad news, but any data recovery program will now only recover what is not already overwritten (deleted, but not overwritten). :(

To recover what IS still recoverable, just run **photorec** (or 'extundelete' command, but I haven't yet tried it, so can't say how promising it is).


**EDIT:**
Darkod beat me to it ! :/
Amazing it took me 10 minutes to write the post. Guess I was too busy enjoying the rain while writing it..

---

### Post by lablouw on 2013-06-17
Thanks for the advice guys, I'll keep going at it and will have a look at the extundelete command too. Does the fact that the old home folder was encrypted have any bearing on the recovery software being able to recover (if the files still exist)? Or would it return garbage for anything that was in that folder?

Thanks again.

---

### Post by varunendra on 2013-06-17
> **lablouw said:**
> Does the fact that the **[COLOR="#FF0000"]old home folder was encrypted[/COLOR]** have any bearing on the recovery software being able to recover (if the files still exist)? Or would it return garbage for anything that was in that folder?

Oh my...!
File(s) recovered from previous Home folder would be garbage unless there is a way to decrypt them after recovery. Seems possible but I'm not much aware of encryption-decryption operations, so can't offer much help on that.

Also, since the default setting of PhotoRec is to drop any files that 'seem corrupt' to it, it may not recover those files at all (unless it has the ability to recognize encrypted file headers). In that case, it may help to mount the partition in the same encrypted environment, then re-run photorec. The word 'chroot' comes to mind, but to be honest, I have absolutely no idea what I'm talking about here. Only thing I know is that encryption IS a problem.

Another thing I know is that you can change the settings of photorec to NOT drop corrupt files. It may be helpful if it drops the encrypted file(s) thinking they are corrupt, but will also return a pile of actually corrupt/broken files.

I hope someone experienced with encryption/decryption may offer some real help here. If someone has any ideas, please jump in !

---

### Post by darkod on 2013-06-17
I would try testdisk first, you seem to have started with it. The reason being that testdisk recovers partitions (partition tables), not files one by one. With little luck, you can get back the table structure, and once your "old" partitions are back try to decrypt with the password that you know.

Some files will be corrupted, but most should be there since a default ubuntu install is barely 4GB. It can't overwrite too much.

I wouldn't use photorec first, because it tries file by file, as long as you have a testdisk option on the table.

---

### Post by varunendra on 2013-06-17
> **darkod said:**
> I would try testdisk first, you seem to have started with it. The reason being that testdisk recovers partitions (partition tables), not files one by one. With little luck, you can get back the table structure, and once your "old" partitions are back try to decrypt with the password that you know.

Makes a lot more sense if the partition was formatted. I'm not sure about that. I thought only the existing files get deleted, not that the partition is formatted.

So yeah, if the partition was formatted, there is a good chance to be able to recover the old partition table, and thus the old partition with old files (even if some are corrupt) on it. If that happens, then there is a well documented method to recover encrypted files.

Thanks for the pointer darkod.

---


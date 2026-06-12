---
title: "FileZilla fzcli command prompt not available 20.04.4 LTS"
date: 2022-05-31
forum: Installation &amp; Upgrades
---

### Post by markman8 on 2022-05-31
Hello to all,

Recently I have installed Ubuntu 20.04 on a VM and installed the filezilla package (I suppose that this also includes the filezilla-common package). I only have available the command prompt on this VM and not the desktop.

I have prepared a bash file for running several commands also including a script file (generated dynamically through the bash file) that should run via fzcli command.  

I have tried to run the command from the command prompt (fzcli) calling this generated script but I found with astonishment that ... there is no fzcli command on my VM!!!  I have looked into it through the Internet and I found no such problem as not be able to find the fzcli command after installing the package filezilla normally via apt.  

The only thing that is referred is a filezilla pro for windows and I do not know if same thing applies for linux.  Do I have to download something more to be able to use command line filezilla?

Thank you in advance
markman8

---

### Post by TheFu on 2022-05-31
From a shell/CLI, use sftp or scp or rsync to transfer files to/from any network address.  On ubuntu systems, only the "ssh" package needs to be installed for this to work. It is safe for use over the internet, assuming you setup ssh-keys. Don't use passwords over the internet.

From Windows, you can use the built-in sftp or scp included with the MSFT support for ssh too.  The creation of keys is the same (except file path differences).  Sadly, MSFT didn't include the ssh-copy-id command for some reason. Unix systems have had ssh-copy-id at least 20 yrs to make transferring public keys to the remote system really easy.

I think WinSCP is the competitor to FileZilla on Windows.

But really, it would be best if you learn to use the ssh tools on Unix systems. Leave behind the bloated Windows-centric stuff sooner than later.

sftp uses the same commands that plain ftp uses, so get/mget, put/mput work as expected, just through a secure tunnel between the systems.  sftp accepts the same batch scripts that plain ftp would accept.  If you will be refreshing files, check our rsync.  It is an amazing tool and commonly scripted.

---

### Post by markman8 on 2022-05-31
Yes I suppose that I have to go with the public/private ssh key option here and use scp or sftp.  But still I cannot understand how FileZilla pages describe a whole section on fzcli and how to use the command prompt interface for transfering files.

Yes WinSCP is the one I have used on a local machine running windows and batch scripts to complete the task.  Now that I finally moved to Ubuntu I am translating the same script to bash file.  I will find a way around as you described.

Thank you very much!

---

### Post by TheFu on 2022-05-31
There are many, many, many, convenience aspects with ssh, which make any ssh-based tool (there must be 50 of those) extremely useful and convenient.  Master ssh-based tools and you'll almost never need/want anything else for connections/transfers between different systems.  

If you aren't finding it the easiest way to connect two systems, then likely doing the wrong or hard way with ssh.  
[https://project-awesome.org/moul/awesome-ssh](https://project-awesome.org/moul/awesome-ssh) has some more ideas.

---


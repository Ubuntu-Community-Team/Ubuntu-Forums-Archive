---
title: "SSh install problem."
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by sandyHadoop on 2011-03-16
Hi.
 Iam trying to install Hadoopo single node cluster in my system. When i executed a command, "ssh localhost"   I got am error, saying that  "connect to host localhost port 22: Connection refused". I have checked whether ssh is enabled or not by using command " ps ax | grep [s]shd"  . Then i found that ssh is not enabled.  So i executed a command " sudo /etc/init.d/ssh start" to start the ssh, at this time i got an error that " /etc/init.d/ssh    command not found" . After that i found that SSH is not been installed. In UBUNTU SOFTWARE CENTER I have tried to install  "secure shell(ssh) server", but it wasn't installed showing en error that "The installation or removal of a software package failed.".

PLease please help me out to install the ssh.

Thank you in advance.

---

### Post by kagerato on 2011-03-16
Since you seem to have an idea of how to run console/terminal commands, you can just use this:

```
sudo apt-get install ssh
```That will install both the server and the client.  If you want only one or the other, install 'openssh-client' or 'openssh-server'.

Configuring SSH, on the other hand, is far more complicated.  Hopefully the default settings are good enough / secure enough for you.  Otherwise you're in for reading a lot of documentation :)

If you intend to run the SSH daemon (sshd) for other clients to connect to the current machine, you need to issue:

```
sudo /etc/init.d/ssh restart
```To run it.  There are some limited docs at [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)  .  However, those just scratch the surface.  SSH has more configuration options than anyone in their right mind knows what to do with.

---

### Post by sandyHadoop on 2011-03-16
Hi.  Thank you very much for your reply.

 The link  you have sent  " https://help.ubuntu.com/community/SSH/OpenSSH/Configuring" is after installing the SSH . But when i execute " sudo apt-get install ssh" command i got an error saying that 
" Errors were encountered while processing:
 /var/cache/apt/archives/openssh-server_1%3a5.5p1-4ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)"

When i start working on that error, i got a solution that,  some unwanted package has been installed and need to be deleted. Iam not getting whether i need to delete that or not.

Please help me out of that. 
Thanks a lot.

---

### Post by kagerato on 2011-03-16
dpkg error code 1 is pretty generic, I think.  If there's a specific meaning to that error code, I don't know of it.

Try deleting the DEB file that it fails to install.  Files in /var/cache/apt/archives will be downloaded again as necessary.

---

### Post by sandyHadoop on 2011-03-16
Thank you very much for your guidance.


I have tried with " sudo apt-get update" command which was a solution i found in some site. After this i have tried this command " sudo apt-get install openssh-server ". But this time i got different error saying that,

"  You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.12.1-0ubuntu6) but 2.12.1-0ubuntu10.2 is to be installed
 libc6-dev : Depends: libc6 (= 2.12.1-0ubuntu10.2) but 2.12.1-0ubuntu6 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution). "

So i have tried with "sudo apt-get -f install " so i got error that   "Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.12.1-0ubuntu10.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1) " . 

Please help me how to proceed further.

Thank you very much.

---


---
title: "SSH install problem"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by robertc on 2008-03-27
Hi,

I am using Ubuntu 6.0.6 and trying to use ssh to talk to my server. I'm sure this used to work, now I get the following:

robert@Master:~$ ssh
ssh: symbol lookup error: ssh: undefined symbol: SSLeay

or

robert@Master:~$ ssh 192.168.8.1
ssh: symbol lookup error: ssh: undefined symbol: SSLeay

I have tried un-installing and reinstalling the SSH packages and libraries and it seem to make no difference. What have I mucked up and how do I get it to work again.

Many thanks

Robert

---

### Post by DBrocks on 2008-03-27
> **robertc said:**
> Hi,

I am using Ubuntu 6.0.6 and trying to use ssh to talk to my server. I'm sure this used to work, now I get the following:

robert@Master:~$ ssh
ssh: symbol lookup error: ssh: undefined symbol: SSLeay

or

robert@Master:~$ ssh 192.168.8.1
ssh: symbol lookup error: ssh: undefined symbol: SSLeay

I have tried un-installing and reinstalling the SSH packages and libraries and it seem to make no difference. What have I mucked up and how do I get it to work again.

Many thanks

Robert

Okay. I have dabbled in the SSH world before. On your server, run 

```
sudo apt-get install sshd
```

This will install the ssh server on your server.

Then, you should be able to run 

```
ssh 192.168.8.1
```
also, does your server have a static IP, or is it on a DHCP lease?

Okay, also, SSH may have gone bad on your Computer you are SSHing from. So

```
sudo apt-get --purge remove ssh
```
Will totally remove the ssh on the computer you are SSHing from.

then

```
sudo apt-get install ssh
```
will reinstall it.

Good luck!

---


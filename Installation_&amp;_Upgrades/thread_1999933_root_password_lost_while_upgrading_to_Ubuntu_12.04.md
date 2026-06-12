---
title: "root password lost while upgrading to Ubuntu 12.04"
date: 2012-06-08
forum: Installation &amp; Upgrades
---

### Post by Claude Rebeck on 2012-06-08
While studying "Learning the Shell"
As I try terminal entries, I GET 'Permission Denied". Then
I try "su" to become the root user. When I use the password
that I entered as I installed Ubuntu 11.04, I get Authentication
failure. and cannot use the lesson commands.

 I am the sole user and should be able to be root user.
when I am a user (not root) the password I use after the
session timed out works properly.

When I updated to Ubuntu 12.04, I had no opportunity to enter a password.  How do I get to What the computer has for root password?

---

### Post by wilee-nilee on 2012-06-08
You would use 
```
sudo -i
```to get a root terminal.

There is no actual root password.

---

### Post by varma1993 on 2012-06-08
Claude it looks like you are confused between the sudo password and the root user password. Both are different.
By default the root user password is not set in ubuntu..
you gotta do it on your own..
type this in your terminal:
<snip>
This allows you reset your root password without the old root password.

---

### Post by sisco311 on 2012-06-08
> **Claude Rebeck said:**
> While studying "Learning the Shell"
As I try terminal entries, I GET 'Permission Denied". Then
I try "su" to become the root user. When I use the password
that I entered as I installed Ubuntu 11.04, I get Authentication
failure. and cannot use the lesson commands.

 I am the sole user and should be able to be root user.
when I am a user (not root) the password I use after the
session timed out works properly.

When I updated to Ubuntu 12.04, I had no opportunity to enter a password.  How do I get to What the computer has for root password?

Please check out: [uhelp]community/RootSudo[/uhelp]

If you have any further questions, please feel free to ask.

varma1993 is right, the root password is locked by default in Ubuntu. 

If you read the RootSudo link, you will find out why it's locked. And you will also find information about setting and locking the root password.

---

### Post by varma1993 on 2012-06-10
> **Claude Rebeck said:**
> While studying "Learning the Shell"
As I try terminal entries, I GET 'Permission Denied". Then
I try "su" to become the root user. When I use the password
that I entered as I installed Ubuntu 11.04, I get Authentication
failure. and cannot use the lesson commands.

 I am the sole user and should be able to be root user.
when I am a user (not root) the password I use after the
session timed out works properly.

When I updated to Ubuntu 12.04, I had no opportunity to enter a password.  How do I get to What the computer has for root password?
Claude it looks like you are confused between the sudo password and the root user password. Both are different.
By default the root user password is not set in ubuntu..
you gotta do it on your own..
type this in your terminal:
sudo passwd
This allows you reset your root password without the old root password.

---

### Post by varma1993 on 2012-06-10
> **Claude Rebeck said:**
> While studying "Learning the Shell"
As I try terminal entries, I GET 'Permission Denied". Then
I try "su" to become the root user. When I use the password
that I entered as I installed Ubuntu 11.04, I get Authentication
failure. and cannot use the lesson commands.

 I am the sole user and should be able to be root user.
when I am a user (not root) the password I use after the
session timed out works properly.

When I updated to Ubuntu 12.04, I had no opportunity to enter a password.  How do I get to What the computer has for root password?
Claude it looks like you are confused between the sudo password and the root user password. Both are different.
By default the root user password is not set in ubuntu..
you gotta do it on your own..
type this in your terminal:
sudo passwd
This allows you reset your root password without the old root password.

---

### Post by Claude Rebeck on 2012-06-20
Thanks for the help!!   Problem solved

---


---
title: "Edgy won't upgrade to Feisty"
date: 2007-08-20
forum: Installation &amp; Upgrades
---

### Post by lakelovers on 2007-08-20
Yesterday I used the official command for upgrading to Feisty. After an all-night and  all-morning download, I lost my DSL (which was moving at the blazing speed of a turtle). Of course the upgrade was aborted. So now I have my DSL, running but when I put in the command 
$ gksu "update-manager -c" I get the message that my system is up to date. That same command started the upgrade yesterday. So, what's the deal? How do I proceed? By the way I get this error message immediately after executing the command:
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

I got the same thing yesterday, but the upgrade seemed to be moving along fine. What does that error mean and should I be concerned?

**Edit**
Well, don't know why/how but I tried again, and the upgrade  went to work, but the download is incredibly slow. My DSL provider says the line speed is where it should be so, he says, that the download source server has to be slow. Is this true of Ubuntu servers?

**Edit 2**

Rats. . . the download quit before it was barely started. The message said the problem was probably my internet connection. I live in the boonies and have a coop Tel company DSL. I have no choice of ISP's with DSL. So I live with it.

---

### Post by stchman on 2007-08-20
> **lakelovers said:**
> Yesterday I used the official command for upgrading to Feisty. After an all-night and  all-morning download, I lost my DSL (which was moving at the blazing speed of a turtle). Of course the upgrade was aborted. So now I have my DSL, running but when I put in the command 
$ gksu "update-manager -c" I get the message that my system is up to date. That same command started the upgrade yesterday. So, what's the deal? How do I proceed? By the way I get this error message immediately after executing the command:
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

I got the same thing yesterday, but the upgrade seemed to be moving along fine. What does that error mean and should I be concerned?

I have never had much luck with the upgrade route.  A fresh install would be the best.

---

### Post by lakelovers on 2007-08-20
I have the install CD, but I've resisted going that route because I want to keep my files. I do have most of my files backed up but I don't trust Sbackup which I've been using because it doesn't always do what it's supposed to do. Got some tips for me to make this easier? When I upgraded to Edgy, it went pretty smoothly except I had to manually set up the Xserever.

Jerry

---

### Post by lakelovers on 2007-08-20
I give up. I'm going for a fresh install. Cross your fingers.

Bob. . . I like your website. I've bookmarked and I'm sure I'll find it quite useful.

---


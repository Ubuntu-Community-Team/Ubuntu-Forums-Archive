---
title: "automatic sha256 comparison"
date: 2012-02-27
forum: Installation &amp; Upgrades
---

### Post by MoebusNet on 2012-02-27
I know there must be an easy way to do this, but duck duck go & google haven't been friendly on this so:

[https://help.ubuntu.com/community/HowToSHA256SUM]("https://help.ubuntu.com/community/HowToSHA256SUM")

Instructions state:

"First download the SHA256SUMS and SHA256SUMS.gpg files to the same directory as the iso. Then run the following commands in a terminal."

i haven't been able to download for example:

[http://releases.ubuntu.com/oneiric/SHA256SUMS]("http://releases.ubuntu.com/oneiric/SHA256SUMS")

because it just opens the page in a tab in Firefox but does not offer a download option.

What am I missing? TIA

---

### Post by ottosykora on 2012-02-27
there are two files in that folder:
[http://releases.ubuntu.com/oneiric/](http://releases.ubuntu.com/oneiric/)

you can see one 
SHA1SUMS                                 13-Oct-2011 11:13  633   
SHA1SUMS.gpg                             13-Oct-2011 11:13  198 

so the first one is for the 'manual' check, that means you will produce the sum and see if the line in the text given is the same, the other one will work according the howto link you found with the gpg/pgp contained in your ubuntu distro.

---

### Post by MoebusNet on 2012-02-28
@ottosykora: Thanks for replying. However:

To clarify, my problem is that I cannot "download"

SHA1SUMS.gpg 13-Oct-2011 11:13 198

or

SHA1SUMS 13-Oct-2011 11:13 633

either one. When I left-click either link, Firefox merely opens a new tab displaying the file contents, unlike the .iso file which offers a download option. Right-click does not offer a download option either. Since the instructions clearly require a "download to same directory as the .iso" I am not sure how to proceed.

I welcome advice on how to get over this obstacle.

---

### Post by ottosykora on 2012-02-28
as those are simple text files, you right click on it and select save target as...to get them as files, otherwise the contents are displayed and you would nee to save them as file.

BTW: you will find this behaviour on other ftp servers too. The browser is doing that simply.

The thing is, that often people do import and handle those contents directly as they see it, copy the gpg signatures to clipboard and work with it without making a file of it.

---

### Post by MoebusNet on 2012-02-28
Thank you! I thought it might be something simple, I just never have done it that way before.

One last thing: When I

```
gpg --verify SHA256SUMS.gpg SHA256SUMS
```

I get

```
gpg: Signature made Sun 19 Feb 2012 11:28:31 AM CST using DSA key ID FBB75451
gpg: Can't check signature: public key not found
```

is this something I'm doing wrong or is there something else going on?

---

### Post by ottosykora on 2012-02-29
well yes, the gpg file is the signature of the other file. The idea is you can check that nobody did place wrong sum file on the server.

To check with gpg, you have to include the public key in your keyring.

This all is kind of complicated now, as there is no nice gui for this tasks on 11.10, so all has to be done with command line.

follow instruction here:
[https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto)

scroll down for obtaining the public key

---

### Post by MoebusNet on 2012-02-29
Doh! I wasn't aware of that layer of verification. I guess I'll have to dig a little deeper into the Ubuntu documentation.

Thank you very much for your time and effort.

I'll mark this thread as "SOLVED".

---

### Post by ottosykora on 2012-02-29
> **MoebusNet said:**
> Doh! I wasn't aware of that layer of verification. I guess I'll have to dig a little deeper into the Ubuntu documentation.

Thank you very much for your time and effort.

I'll mark this thread as "SOLVED".

I have seen some people complaining about this complexity, but if you observe it, there is no other way at all.
The checksum is to check if the downloaded file was downloaded complete, as it often happens that download stops somewhere in the middle or the file is otherwise broken.
So the checksum (hash) is just to check physically the file itself.

As all is on a server and on lot of mirrors etc, both files, the .iso and the checksum could be replaced.

To make it simple, only the checksum file is signed with detached signature. 
PGP/GPG uses 'web of trust' system to verify if keys are genuine and as signature of a file rather difficult if not impossible to fake, you are then pretty sure the iso you obtained is 
1.complete AND 2.it is original one

To avoid any other special software needed for verification, gpg, which is installed on many distros by default is used for this.

---


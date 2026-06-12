---
title: "Creation of own repositories"
date: 2006-12-13
forum: Installation &amp; Upgrades
---

### Post by Christian.Hutter on 2006-12-13
Hi,

I need to provide some preconfigured software packages for our  Ubuntu users so I'm trying to setup and use my own repository. Now I'm stuck and don't know what to change to get this working. Hopefully someone can help me...

My problem is that I can't get secure APT working. I did create a basic http based repository which only hosts binary packages unter <document-root>/ubuntu/binary and created a new entry in sources.list "deb <servername>/ubuntu binary/"

In the binary dir of the web server I did only have the .deb package and a Release file. When using "apt-get update" I did get an authentication warning but  i could install the packages.

So on the next step I did add the md5sum hashes to the Release file, created an gpg key and used it to sign the Release file. Then I did export the public key and imported it on the client using apt-key add

Now running apt-get update I get 

W: GPG error: http://<servername> binary/ Release: Unknown error executing gpgv

This is my Release file
[INDENT]
Origin: UdL
Label: UdL
Suite: Edgy
Version: 6.10
Codename: edgy
Architectures: any
Components: main
MD5Sum:
cf33c8607028041ebe8f535eee299481  Packages.gz
268ad687e7a7faa9bc0ae4fe0f4152df  udl-ntp_0.2-1_i386.deb
[/INDENT]

If I run gpg --verify Release.gpg on the repository server I get "Good signature"

"apt-key list" on the client shows the key and doesn't report a problem

Does someone have an idea why I still get that error message???

Thanks for your help,
 Christian

---


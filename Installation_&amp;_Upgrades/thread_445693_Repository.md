---
title: "Repository"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by Aramis76 on 2007-05-16
Hello,

I got a very specific question about package repositories.  I want to build my own repository server for internal use.  I installed Ubuntu on a testing partition and installed the packages I need.  Now I want to copy these packages to an FTP-server so I can install these packages on my other PCs.

You might ask why not installing these packages straight from the Ubuntu repositories?
I got 2 reasons to do it on a local server :

1) This way I save bandwidth on my internet connection (this is not the main reason, because it will only be using bandwidth when the packages are downloaded)
2) In Belgium you are limited with the amount you can download per month, and this way I can reduce this as well
3) Just to learn is a good reason too, isn't it :)

Now where is the problem?  I copied the packages to my server, but now I need to create the necessary files so apt-get can see it as a repository.  How do I have to do this?

Thanks in advance,
Aramis

---

### Post by ajgreeny on 2007-05-16
If you just need to save bandwidth, just download the packages you need without installing at all, or just install to the one computer, then copy all the files in /var/cache/apt/archives to the same folder on the other computers.  Then when you use apt-get or synaptic the system will find the debs and install them without downloading.  You could also write them to a cd and add that to your sources.list file.

---


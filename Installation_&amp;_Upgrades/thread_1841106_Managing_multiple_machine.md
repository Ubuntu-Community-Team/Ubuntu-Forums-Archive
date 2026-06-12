---
title: "Managing multiple machine"
date: 2011-09-08
forum: Installation &amp; Upgrades
---

### Post by Jonny87 on 2011-09-08
I will soon be managing multiple laptops and computers which will all be running the same version of Ubuntu (or possibly Kubuntu) 11.04.
While some will some different apps than others for the most part they will almost identical. I want to know is there an easy way that I can manage updates etc so that they aren't all downloading the same updates from the internet? So one system downloads them once then the rest do get them from that machine, this would help to reduce the download quota being used up. 

I don't know, is it possible to set one up as update server that I can point the rest to? I still want each comp user to be able to download their own apps as they need to, even if the other comps users don't have it or use it.

Any ideas?

---

### Post by haqking on 2011-09-08
> **Jonny87 said:**
> I will soon be managing multiple laptops and computers which will all be running the same version of Ubuntu (or possibly Kubuntu) 11.04.
While some will some different apps than others for the most part they will almost identical. I want to know is there an easy way that I can manage updates etc so that they aren't all downloading the same updates from the internet? So one system downloads them once then the rest do get them from that machine, this would help to reduce the download quota being used up. 

I don't know, is it possible to set one up as update server that I can point the rest to? I still want each comp user to be able to download their own apps as they need to, even if the other comps users don't have it or use it.

Any ideas?


I think you mean like WSUS in windows ?

not sure, i imagine you could somehow, as an update location is from the sources list which points to URL.

So in theory you could, but no direct experience of this, perhaps someone else will chime in.

I have it in my head to have one server point to the repos, and your clients point to your server so i imagine it can be done ?

after all its what all our machines do on the internet to the repos ;-)

---

### Post by Jonny87 on 2011-09-08
> **haqking said:**
> I think you mean like WSUS in windows ?

not sure, i imagine you could somehow, as an update location is from the sources list which points to URL.

So in theory you could, but no direct experience of this, perhaps someone else will chime in.

I have it in my head to have one server point to the repos, and your clients point to your server so i imagine it can be done ?

after all its what all our machines do on the internet to the repos ;-)

Yea exactly WSUS is probably the best example of what im after. If I was windows I'd be looking at setting up WSUS.

---

### Post by rolandrock on 2011-09-08
I too have never tried it but this guide looks pretty close:
[http://www.debian-administration.org/articles/286](http://www.debian-administration.org/articles/286)

---

### Post by Jonny87 on 2011-09-08
> **rolandrock said:**
> I too have never tried it but this guide looks pretty close:
[http://www.debian-administration.org/articles/286](http://www.debian-administration.org/articles/286)

Sounds interesting, will keep it in mind. Though i'm wondering, is that the best solution for a local network? or is there another way to achieve the same sort of thing for a local network?

---

### Post by rolandrock on 2011-09-08
I think the guide describes a local network.  Are you trying to avoid using apache on the server?  You could mount the directory containing the updates on the client machines then point the sources.list entry using a file:// prefix instead of http:// perhaps?

---

### Post by Jonny87 on 2011-09-08
> **rolandrock said:**
> I think the guide describes a local network.  Are you trying to avoid using apache on the server?  You could mount the directory containing the updates on the client machines then point the sources.list entry using a file:// prefix instead of http:// perhaps?

So using that method will each system defiantly try the local repository first for any of its downloads?

---

### Post by rolandrock on 2011-09-08
apt-get depends on /etc/apt/sources.list for updates.  If the client machines only have one entry (your server's address) in the sources file, then they will only look on your server.

That is how I understand it to work.

---

### Post by Jonny87 on 2011-09-08
> **rolandrock said:**
> apt-get depends on /etc/apt/sources.list for updates.  If the client machines only have one entry (your server's address) in the sources file, then they will only look on your server.

That is how I understand it to work.

Yea I understand that much already but thats the issue, I want them to have the normal repos as well so they can still download new software unless there is a way to do it via the local server;
i.e. 
Laptop wants to download VLC, Laptop makes request to server,
If server doesn't have the VLC packages (and dependencies), server downloads them from the internet,
Laptop then proceeds to download from local server.
If Laptop2 wants VLC, its already on the local server.

The above example  is an ideal setup, though unnecessary, I'm mainly concerned about the updates, each other comp can still get other software from the internet. I just don't see the point of having 5 or more comps all downloading the same updates form the internet, its a waste of download.

---

### Post by Jonny87 on 2011-09-09
Am i right in saying that if the packages are already in /var/cache/apt/archives/ then they won't be re-downloaded? 

If so what if I set up a script on each system that would copy the packages from the server to the /var/cache/apt/archives/.
And the local server would copy its packages from /var/cache/apt/archives/ to a shared dir.

So server would;
rsync packages to /share

Each comp would;
rsync \\server\share to /var/cache/apt/archives/
then apt-get update

The scripts could be crond to run every couple minutes.

Is there anything majorly wrong with this idea?

---

### Post by Jonny87 on 2011-09-09
**BUMP**
Anyone else got any other ideas or input?

---

### Post by jmate24 on 2011-09-09
install 11.04 server on one machine and make it a file server. then there is a resource on how to do this in: [HTML]https://help.ubuntu.com/community/Apt-Cacher-Server[/HTML].
that should get you started.

---

### Post by rolandrock on 2011-09-09
> Am i right in saying that if the packages are already in /var/cache/apt/archives/ then they won't be re-downloaded? 

If so what if I set up a script on each system that would copy the packages from the server to the /var/cache/apt/archives/.
And the local server would copy its packages from /var/cache/apt/archives/ to a shared dir.

So server would;
rsync packages to /share

Each comp would;
rsync \\server\share to /var/cache/apt/archives/
then apt-get update

The scripts could be crond to run every couple minutes.

Is there anything majorly wrong with this idea?


I don't think that would work.  apt-get won't dpkg and install something just because it has been dumped in its archive directory.

Read and understand the system built in the previously provided link and study apt-get man page.

You may be able to disable automatic updates on the client machines and schedule a job that uses a dedicated source (your server) somehow while still allowing the user to use their standard source.list.  You will still have to build your own repository as described in the previous link.

This seems like a lot of work to save a little bandwidth which is probably why there isn't a great deal of documentation on it.

Good luck.

---

### Post by Jonny87 on 2011-09-09
> **jmate24 said:**
> install 11.04 server on one machine and make it a file server. then there is a resource on how to do this in: [HTML]https://help.ubuntu.com/community/Apt-Cacher-Server[/HTML].
that should get you started.

Thanks I've looked at it and I'll keep that in mind if thers no simpler solution.


> **rolandrock said:**
> I don't think that would work.  apt-get won't dpkg and install something just because it has been dumped in its archive directory.

Read and understand the system built in the previously provided link and study apt-get man page.

You may be able to disable automatic updates on the client machines and schedule a job that uses a dedicated source (your server) somehow while still allowing the user to use their standard source.list.  You will still have to build your own repository as described in the previous link.

This seems like a lot of work to save a little bandwidth which is probably why there isn't a great deal of documentation on it.

Good luck.

Yea I realize that apt-get won't automatically install the package just because they have been dumped there but I thought that by having them copied there, then they would be used the next time it was told to update or install an app. Just an idea that I had.
Yea the whole server thing does seem like alot of work just to save bandwidth, thats why I'm looking for a simpler solution.
I'm not worried bout setting up servers though, have done it before and am willing to again. I'm currently running an ftp server at home at the moment.

---

### Post by Jonny87 on 2011-09-10
> **jmate24 said:**
> install 11.04 server on one machine and make it a file server. then there is a resource on how to do this in: [HTML]https://help.ubuntu.com/community/Apt-Cacher-Server[/HTML].
that should get you started.

Two questions on this;
Is apache needed (i.e. could it be used over samba)?

Is the article still valid (it mentions Jaunty as being a newer version)?

---


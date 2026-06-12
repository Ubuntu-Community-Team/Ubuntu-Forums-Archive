---
title: "[SOLVED] Synaptic problem on Xubuntu"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by atomic_turtle on 2007-04-20
Hi all,

I've got a Dell subnotebook - an older model - with Ubuntu installed. I changed the Desktop to Xfce and upgraded to Dapper.
Now I'd like to put KDE on as I'm using that on my Desktop, so I know it's look and feel - I'm not sure whether it'll run as fast then, but I'll see about that. Also, I'd naturally like to install some stuff to turn that notebook into a serious work tool.
Now, my problem is something about my synaptic is wrong. When I try to update my repos, I get an error message, listing more or less all of them and telling me there was an error resolving the host names. After fuzzing around with it a bit, I decided that copying the file from my desktop would be best because the base system is the same, only different desktop. I don't have any problem whatsoever updating the repos on my Desktop and installing stuff.
To give you a good shot at my problem, I post my /etc/apt/sources.list here:

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy universe
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse

(of course, it says "dapper" and not "edgy" everywhere, this is the file from my desktop - I've adapted it of course, there's Dapper running on the Notebook.
I'd really appreciate some help on this one because without a possibility of installing stuff, I'm lost...
Thanks a lot!
Regards,

atomic_turtle

---

### Post by atomic_turtle on 2007-04-24
Hi,

I searched for a solution for this a while and now it seems the problem is somewhat different: It seems that all my network interfaces are off by default and I have to activate them. That's no problem, I have the data I need from my Desktop. The problem is this:
- Yesterday, my router gave up its service temporarily while I was just downloading a series of packages via Synaptic on my notebook. In the meantime, it's okay again, but I guess now there are a couple of broken packages on my notebook, so I don't know if it's going to be all right when I just try to repair them now. I'll try, anyway.
Regards,

atomic_turtle

---

### Post by atomic_turtle on 2007-04-25
Hi,

I haven't got a clue how I can mark a thread as solved here - on ubuntuusers.de, for instance, there's an option and the thread gets a green tick like a V - I've edited it in the title of this post, but that's not the easiest option. Is there an easier one?
Anyway, this thread is solved. My problem wasn't about Synaptic, it turned out to be about the network interfaces and now it's fixed.
Regards,

atomic_turtle

---


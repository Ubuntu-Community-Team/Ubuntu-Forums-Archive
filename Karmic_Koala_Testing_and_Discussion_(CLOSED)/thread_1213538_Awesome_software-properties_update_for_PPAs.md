---
title: "Awesome software-properties update for PPAs"
date: 2009-07-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jpeddicord on 2009-07-14
Was poking through changelogs today, and saw software-properties had a new version out: [https://edge.launchpad.net/ubuntu/+source/software-properties/0.75/+changelog](https://edge.launchpad.net/ubuntu/+source/software-properties/0.75/+changelog)```
  * new helper script "add-apt-repository" that can be used to
    enable a repository from the commandline. Useful for e.g.
    'add-apt-repository ppa:gnome-desktop'

```

I gave it a try with `sudo add-apt-repository ppa:jpeddicord`. Not only did it add an entry to sources.list.d, it also fetched the GPG key automatically.

Out of curiosity, I opened software-properties-gtk (system > admin > software sources) and tried to add a PPA on the third-party software tab.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=121117&d=1247626744[/IMG]

Using the same syntax for the add-apt-repository command, it worked. Didn't appear to grab the GPG key at first, but after restarting the interface the key was indeed there.

This is awesome, and definitely lowers the barrier for adding PPAs to a system. Hopefully this functionality will continue to improve. :)

---

### Post by ghindo on 2009-07-14
Very, very cool.

---

### Post by alphacrucis2 on 2009-07-14
Nice!

---

### Post by Starks on 2009-07-14
Ever since the authentication prompts became more prominent, I've been wanting this.

---

### Post by gnomeuser on 2009-07-15
That is very neat, I would though still prefer that work be focused on upstream PackageKit than our own complete suite of tools. It would make life so much easier and more pleasant.

---

### Post by loell on 2009-07-15
hunting gpg keys is a thing of the past. :)

---

### Post by drubin on 2009-07-15
I think although  this is a good idea. It kinda making even having a key useful.. If it auto gets keys for a repo.

I sense this becomeing a windows mentality for installing dodgy 3rd party application.

---

### Post by ELD on 2009-07-15
So i won't have to search for the GPG key any longer, save it to a blank file and then import it...?

---

### Post by taavikko on 2009-07-15
> **ELD said:**
> So i won't have to search for the GPG key any longer, save it to a blank file and then import it...?

You haven't had to do that in ages ;)
But answering your guestion, yes, that command will do it for you.

---

### Post by ELD on 2009-07-15
I actually have or it complains i don't have they key.

---

### Post by martinpm24 on 2009-07-15
great! :)

---

### Post by taavikko on 2009-07-15
> **ELD said:**
> I actually have or it complains i don't have they key.

I meant that "sudo apt-key adv --options here key-id here" is sufficient :)

---

### Post by Vadi on 2009-07-15
The auto-key fetching is nice. Still a whole procedure to add a PPA and install something from it, though.

---

### Post by Gourgi on 2009-07-15
Also a decent way to discover which files are present in a PPA would be great! 
Something like this maybe [http://ubuntuforums.org/showpost.php?p=6882449&postcount=43](http://ubuntuforums.org/showpost.php?p=6882449&postcount=43) ):P

---

### Post by lukeen on 2009-07-15
Very nice!
So far my easiest way of adding a PPA: [http://lukeen.blogspot.com/2009/06/easy-way-to-search-and-add-launchpad.html](http://lukeen.blogspot.com/2009/06/easy-way-to-search-and-add-launchpad.html)

---

### Post by RainCT on 2009-07-15
> **Gourgi said:**
> Also a decent way to discover which files are present in a PPA would be great!

[https://edge.launchpad.net/ubuntu/+ppas](https://edge.launchpad.net/ubuntu/+ppas)

---

### Post by durand on 2009-07-15
At this point, wouldn't it be possible to have a ppa:// wrapper script like we do for apt?

---

### Post by Starks on 2009-07-15
Gripe.

Repos are added to /etc/apt/sources.list.d instead of sources.list

---

### Post by durand on 2009-07-15
> **Starks said:**
> Gripe.

Repos are added to /etc/apt/sources.list.d instead of sources.list

How is that a problem? /etc/apt/sources.list still works as expected.

---

### Post by Starks on 2009-07-15
Yes, but if I want to remove the repos, I have to edit/remove the files manually. I can't do that using the graphical interface for add/removing repos.

---

### Post by durand on 2009-07-15
Oh, you're right about that. Sorry, didn't notice that problem...

---

### Post by ghindo on 2009-07-15
> **Starks said:**
> Gripe.

Repos are added to /etc/apt/sources.list.d instead of sources.listFile a bug?

---

### Post by durand on 2009-07-15
> **ghindo said:**
> File a bug?

Maybe you should file a bug towards software-sources about not looking in the sources.list.d directory.

---

### Post by Starks on 2009-07-15
Here's the bug I filed.

[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/399898](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/399898)

---

### Post by vinutux on 2009-07-15
sounds...good

---

### Post by MadMan2k on 2009-07-15
> **gnomeuser said:**
> That is very neat, I would though still prefer that work be focused on upstream PackageKit than our own complete suite of tools. It would make life so much easier and more pleasant.
will not happen. packagekit is designed in a incompatible way to debian packages. [http://www.glatzor.de/blog/blog-details/article/aptdaemon/?tx_ttnews](http://www.glatzor.de/blog/blog-details/article/aptdaemon/?tx_ttnews)[backPid]=4&cHash=2fe858b71b

---

### Post by snkiz on 2009-07-16
> **taavikko said:**
> I meant that "sudo apt-key adv --options here key-id here" is sufficient :)

Still have to find the key id then, and when I reinstall I'll have to do that all over again. lets see something that puts the keys in a place that they would survive a upgrade/reinstall (ie: home dir) and have apt search that dir for keys first.

---

### Post by taavikko on 2009-07-16
> **snkiz said:**
> Still have to find the key id then, and when I reinstall I'll have to do that all over again. lets see something that puts the keys in a place that they would survive a upgrade/reinstall (ie: home dir) and have apt search that dir for keys first.

hmm,. no you don't, when trying to "apt-get update" it throws the warning on unauthenticated repos, and gives you the key, eg. 1024/12345678 where the 12345678 is the key-id.

and by using seahorse you can export the gnupg keyring to where-ever you desire :)

---

### Post by snkiz on 2009-07-16
> **Starks said:**
> Yes, but if I want to remove the repos, I have to edit/remove the files manually. I can't do that using the graphical interface for add/removing repos. 

works in Jaunty I made a custom sources list and put it there, called it ckubuntu.list works perfect. so it would be a regression then

---

### Post by snkiz on 2009-07-16
> **taavikko said:**
> hmm,. no you don't, when trying to "apt-get update" it throws the warning on unauthenticated repos, and gives you the key, eg. 1024/12345678 where the 12345678 is the key-id.

and by using seahorse you can export the gnupg keyring to where-ever you desire :)

LOL thats what seahorse does? I been wondering that. how does that work?

---

### Post by omegamormegil on 2009-07-18
> **Starks said:**
> Here's the bug I filed.

[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/399898](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/399898)

Well, that one was fixed quick.

---

### Post by ghindo on 2009-07-18
> **omegamormegil said:**
> Well, that one was fixed quick.That's open source software for you ;)

---

### Post by Regenweald on 2009-07-31
This needs a bump.
```

sudo add-apt-repository ppa:exaile-devel

```

went perfectly :)

---

### Post by Greg K Nicholson on 2009-09-06
Is it possible to add the Medibuntu repositories this way?

---

### Post by jmmL on 2009-09-06
> **Greg K Nicholson said:**
> Is it possible to add the Medibuntu repositories this way?

I would imagine that since medibuntu repos are hosted by themselves and not on launchpad that it is probably not possible to add them this way.

---

### Post by 23meg on 2009-09-06
> **Greg K Nicholson said:**
> Is it possible to add the Medibuntu repositories this way?

No, since it's not a PPA. The main point of the PPA service is building things from source, and Medibuntu includes lots of closed-source software.

---

### Post by MadMan2k on 2009-09-06
> **23meg said:**
> No, since it's not a PPA. The main point of the PPA service is building things from source, and Medibuntu includes lots of closed-source software.
well this refers to building packages from source, not necessarily the applications. basically there is no technical reason why medibuntu cant be a PPA.

---

### Post by 23meg on 2009-09-06
> **MadMan2k said:**
> well this refers to building packages from source, not necessarily the applications. basically there is no technical reason why medibuntu cant be a PPA.

Right, hence my saying "point"; there's not much *point* in it being a PPA, and in any case 
[the terms of use for the PPA service]("https://help.launchpad.net/PPATermsofUse") restrict the distribution of some of the non-free packages they carry, so that's one reason why it can't.

---

### Post by Starks on 2009-09-29
Anyone noticing that keys aren't being downloaded anymore?

Is the keyserver down?

---

### Post by andrewabc on 2009-09-29
> **Starks said:**
> Anyone noticing that keys aren't being downloaded anymore?

Is the keyserver down?

I've tried getting keys for a month or two and no luck. I figured it was my ISP, but if keyserver is on simple http(s) connection (port 80), then I should be able to get them.

---

### Post by VMC on 2009-09-29
> **Starks said:**
> Anyone noticing that keys aren't being downloaded anymore?

Is the keyserver down?

I think so. I just tried it and it timed out:
```
$ sudo add-apt-repository ppa:jpeddicord
[sudo] password for vmc: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv AFC972CE84C8F020FEAAC5C35ABA245DCC2ACA8F
gpg: requesting key CC2ACA8F from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
```

---

### Post by jpeddicord on 2009-09-29
> **VMC said:**
> I think so. I just tried it and it timed out:
```
$ sudo add-apt-repository ppa:jpeddicord
[sudo] password for vmc: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv AFC972CE84C8F020FEAAC5C35ABA245DCC2ACA8F
gpg: requesting key CC2ACA8F from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
```

Likely intermittent problems; working here.

---

### Post by merlyn on 2009-09-30
Just stumbled across this little gem!

Works a treat thanks!

---


---
title: "Build-essentials help."
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by {Nabla} on 2008-10-19
I'm having a problem installing buid-essentials which means I can't compile anything. (It's really annoying since I don't have the internet on my ubuntu installation, and the guide I'm looking at to install ndiswrapper says I need build-essentials)

I tried:

```
sudo aptitude update && sudo aptitude upgrade && sudo aptitude intstall build-essentials
```

but I keep getting errors that it couldn't find them. Is there any other way to install them?

can I use the synaptic manager?

---

### Post by az on 2008-10-19
You can use whatever package manager you like.  The package is named *build-essential*, not *build-essentials*.

---

### Post by Shazaam on 2008-10-19
Remove the "s" from the end of your command (it's build-essential).


EDIT= rats, foiled again! :)

---

### Post by {Nabla} on 2008-10-19
Thanks both, I will quickly try the suggestions and get back. (which means restart arhhh)

---

### Post by {Nabla} on 2008-10-19
OK I still got the error messages, and since I can't transfer the text file to windows for lack of a usb stick, I will try and describe them:

```
sudo aptitude update && sudo aptitude upgrade && sudo aptitude install build-essential
```

Returned:

> 
[long list of URL's each followed by "Could not resolve gb.archive.ubuntu.com" (I'm guessing it's trying to connect to the internet, and I don't have a connection)]

"The following packages have been kept back:
ssl-cert"

"The "upgrade" command is deprecated use "safe-upgrade" instead"

"No candidate version found for build-essential"


And in between each of those things, is a short list of processes it's doing followed by "...done", but I didn't think that was significant enough to post?

So I tried the same thing with "safe-upgrade" and it returned exactly the same thing, but minus the warning about the upgrade command.

I also looked in synaptic package manager, and there is no entry for 'build-essential', but I did notice some entries called "header 2.6.4." (Or something like that). There was about ten of these with slightly different names. Is that header files for c?

Is there anything else I can try?

---

### Post by zvacet on 2008-10-19
```
gksudo gedit /etc/apt/sources.list
```

and remove # from line 

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted

to look 

deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted

save and close file.

```
sudo apt-get update
```

Put CD in the drive and 

```
sudo apt-get install build-essential
```

---

### Post by {Nabla} on 2008-10-19
Thanks, I'll give that a whirl, and be back soon. :)

---

### Post by {Nabla} on 2008-10-19
Thanks soo much, it worked like a charm. I just compiled and ran a hello world program....Now for ndiswrapper.

---


---
title: "Installing CVS"
date: 2005-06-20
forum: Installation &amp; Upgrades
---

### Post by headswim on 2005-06-20
I'm trying to install CVS so that I can give entrance a shot, but not having much luck.  I installed CVS through Synaptic, and that went off without a hitch.  When I first did that, I was getting errors about CVSROOT.  I set that to /var/lib/cvs since I saw that's where the CVSROOT directory was.  Then, when I tried doing a cvs checkout httpc it would give me an error about checking out the repository into itself.  Since then I installed and am now using the 686 smp kernel, and when I try doing a cvs checkout httpc it gives me the following error:
```

root@mjones:/home/mjones # cvs checkout httpc
cvs checkout: cannot find module `httpc' - ignored

```

Is this due to the new kernel I am using?  If it is, is there a way to fix this?  Also, whether I fix this w/ the 686 kernel, or go back to the 386 kernel which is still installed, where should my CVSROOT be pointing to?  Any help would be appreciated, since I would like to check out entrance.

P.S. No I am not totally new to linux, although it has been a while, and this is also my first time working with a debian based distro.

---

### Post by tread on 2005-06-20
I'm confused, are you trying to setup a cvs server or a cvs client to checkout source from entrance's cvs?

---

### Post by tread on 2005-06-20
If you are trying to setup entrance, follow these instructions: 
[http://get-e.org/User_Guide/English_pages/print.html](http://get-e.org/User_Guide/English_pages/print.html) 

Your only interaction with cvs in this case will be the commands:
```

cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/enlightenment login
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/enlightenment co e17

```

You can install cvs with:
```

sudo apt-get install cvs

```

---

### Post by headswim on 2005-06-20
Sorry, I should've been more specific.  I'm trying to install the client to checkout sources.  I did the apt-get install cvs already, through a root terminal.  That went off without a hitch.  The problem started when I was trying to I thought test the install.  I read in an intro guide off of cvshome.org to do a cvs checkout httpc.  When I try doing that I get errors about the CVSROOT and trying to checkout the repository into itself.  Maybe that has to do with being a server.  This is my first time having to set up cvs this way.  All the previous distros I've used it came bundled.  I'll definitely try it when I get to work in the morning though.  Thanks for the response.

Jones

---


---
title: "[SOLVED] Problems upgrading to 7.10 RC"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by iamthemicrowave on 2007-10-13
I upgraded to 7.10RC about 2 days ago, but there were some errors in the process. My machine is currently workable, but the update manager tells me I have 30 updates to install. When I try to do that , I get the following error message:

E: tzdata: subprocess post-installation script returned error exit status 10
E: util-linux: dependency problems - leaving unconfigured

Then a new window opens and says not all updates were installed. The terminal below has this output:

```

Preconfiguring packages ...
Setting up tzdata (2007f-3ubuntu1) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on tzdata (>= 2006c-2); however:
  Package tzdata is not configured yet.
dpkg: error processing util-linux (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
 util-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up tzdata (2007f-3ubuntu1) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of locales:
 locales depends on tzdata; however:
  Package tzdata is not configured yet.
dpkg: error processing locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-en-base:
 language-pack-en-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on tzdata (>= 2006c-2); however:
  Package tzdata is not configured yet.
dpkg: error processing util-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on locales; however:
  Package locales is not configured yet.
 ubuntu-minimal depends on tzdata; however:
  Package tzdata is not configured yet.
 ubuntu-minimal depends on util-linux; however:
  Package util-linux is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-en:
 language-pack-en depends on language-pack-en-base; however:
  Package language-pack-en-base is not configured yet.
dpkg: error processing language-pack-en (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en-base:
 language-pack-gnome-en-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-jre:
 sun-java6-jre depends on locales; however:
  Package locales is not configured yet.
dpkg: error processing sun-java6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of util-linux-locales:
 util-linux-locales depends on util-linux (>= 2.13-0); however:
  Package util-linux is not configured yet.
 util-linux-locales depends on util-linux (<< 2.13.0-0); however:
  Package util-linux is not configured yet.
dpkg: error processing util-linux-locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en:
 language-pack-gnome-en depends on language-pack-gnome-en-base; however:
  Package language-pack-gnome-en-base is not configured yet.
dpkg: error processing language-pack-gnome-en (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-jdk:
 sun-java6-jdk depends on sun-java6-jre (= 6-03-0ubuntu2); however:
  Package sun-java6-jre is not configured yet.
dpkg: error processing sun-java6-jdk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-bin:
 sun-java6-bin depends on sun-java6-jre (= 6-03-0ubuntu2); however:
  Package sun-java6-jre is not configured yet.
dpkg: error processing sun-java6-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-03-0ubuntu2); however:
  Package sun-java6-bin is not configured yet.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured 
```

---

### Post by jwhitener@optaros.com on 2007-10-16
I have the EXACT same problem. Can anyone shed some light on how to resolve these dependency issues?

---

### Post by moneypenny on 2007-10-16
I'm having the same problem.  update-manager just died out and even when I try to fix things in a term using apt-get or aptitude, I still get a lot of errors:

```
Errors were encountered while processing:
 tzdata
 util-linux
 locales
 language-pack-en-base
 language-pack-gnome-en-base
 language-pack-gnome-ko-base
 language-pack-ko-base
 sun-java5-jre
 sun-java5-bin
 util-linux-locales
 ubuntu-minimal
 sun-java5-plugin
 language-pack-en
 language-pack-gnome-en
 language-pack-gnome-ko
 language-pack-ko
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Wybiral on 2007-10-16
This thread is labeled "solved" but there's not solution :(
I'm having the same problem.

---

### Post by VCSkier on 2007-10-16
Have you tried with Synaptic?  Once or twice it has patched things up for me that apt-get and aptitude could not.

---

### Post by ReyBrujo on 2007-10-16
I followed [this advice]("https://answers.launchpad.net/ubuntu/+question/14519"): change your locale to something else. I had it in America/Buenos Aires, so I went to the clock, right click, adjust date & time, and then changed the time zone to something else (America/Yellowknife in my example). I clicked ok, and then tried *sudo apt-get --fix-broken install* and it worked. Right after, I did *dpkg-reconfigure tzdata* and chose America/Buenos Aires again, and there, solved. Hopefully it will work for you as well.

---

### Post by ReyBrujo on 2007-10-16
By the way, are the ones having this problems the only ones who have installed sun-java* files? I had sun-java6-* files, which are the ones triggering the error, and from what I see in the previous two logs, they also had sun-java* installed.

I still don't know how to continue the upgrade, though, so we are left in a 60% Gusty, 40% Feisty setup.

---

### Post by jwhitener@optaros.com on 2007-10-17
Changing the locale worked. Thanks a lot! :guitar:

---


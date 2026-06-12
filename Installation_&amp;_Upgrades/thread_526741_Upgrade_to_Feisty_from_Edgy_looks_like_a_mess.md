---
title: "Upgrade to Feisty from Edgy looks like a mess?"
date: 2007-08-15
forum: Installation &amp; Upgrades
---

### Post by neander on 2007-08-15
I've had edgy for six months or so and finally clicked the upgrade to 7.04 in the upgrade manager today. After various dialogs spin by

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz) Sub-process gzip returned an error code (1)

I am on a fast internet connection. So anyways I start reading around in this forum. I read some of the sticky 'install the official way' or whatever, a thread that spans close to a year, and man this looks like a nightmare. Right off the bat in that thread people are saying ya the official method hosed my box, and people are still reporting issues like that in the most current postings.

I don't want to send a major amount of time on this. I have a very simple edgy installation. Can I just put in a fawn cd and run an upgrade from there?

---

### Post by linuxwizard on 2007-08-15
Look at the bottom of this page talks about upgrading with CD

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by neander on 2007-08-15
OK, thanks...now, is the upgrade process pretty safe? There are some here that thing a clean install is best and upgrades are 'always a bad idea'.

I suppose if the upgrade hoses the install, I can start over with a fresh install anways, backup before of course.

---

### Post by linuxwizard on 2007-08-15
Yes their are different views on upgrading. One says fresh install & another says upgrade. I know I upgraded my Dapper Ubuntu & Dapper Kubuntu to Edgy on both with no issues at all. I think some of the issues of upgrading is if you use automatix, easyubuntu or if you added alot of different repositories to your source list. That is where problems start. Try upgrading with CD and if you have problems you then know what you will have to do a fresh install.

---

### Post by neander on 2007-08-17
Just wanted to say, I opted for a full reinstall and so far it's been very smooth.

---

### Post by neander on 2007-08-17
Oooo

I screwed it up. I was doing some stuff with bash and dash, and seem to have lost it. sudo no longer worked and when I rebooted it give me a lot of exciting "unable to execute bin/sh" for rcS: not a directory, something like that. 

I wouldn't mind reinstalling for the practice but there is a text file on the desktop that I'd like to recover, it had a shorthand of the steps I took to get 7.04 up and running. I can live without it but...booting from the cd, is there a way to get that doc, save it to floppy or email to myself? I've tried su - root and the pswd for that is not known to me, and su - mylogin, and it reports not valid or something. I started the reinstall process and on step approx 5, no users were found to import from. How can I get to that user's desktop? Not visible from Nautilus, so far.

---


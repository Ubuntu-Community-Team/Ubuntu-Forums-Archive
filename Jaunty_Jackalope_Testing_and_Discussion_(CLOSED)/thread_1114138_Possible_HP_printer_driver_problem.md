---
title: "Possible HP printer driver problem?"
date: 2009-04-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mykrob on 2009-04-02
Running Ubuntu Jaunty on my laptop, which previously had Intrepid. My desktop still is running Intrepid. I have some form letter templates that I use to send out mailers to potential clients, and historically they've worked fine. I did ten letters today, which printed fine. I began printing my first envelope, and it did not print correctly. A lot of text is cut off for some reason. I thought there may be an issue with the built-in Open Office, so I removed it using Synaptic and installed the .debs from the openoffice website, and was able to duplicate the same issue.

I took the same template file to my desktop and attempted to print from there, and printed my envelopes with no problem. Matter of fact, this template has worked fine with this same printer on Hardy and Intrepid.

Since I had the same problem with the onboard Open Office and the one from Sun's website (same that is installed on my Intrepid machine), I don't know if my problem exists somewhere in Gnome or possibly in my printer driver.

the printer is a Hewlett Packard Photosmart C5150. I am trying to print US Business Envelopes, I think they may also be referred to as #10 envelopes.

A test envelope is attached to see if others can duplicate this behaviour.

Any ideas?

Thanks,
-myk

---

### Post by mykrob on 2009-04-03
Bump..

I'm open to suggestions here.

---

### Post by emarkay on 2009-04-03
Yea "Sender" is cut off.

This is what I use - I have the OO from the repos in Jaunty.

---

### Post by mykrob on 2009-04-03
Want to make sure i understand you, you have the same problem? I used the one you attached and it prints with the sender cut off as well.

---

### Post by lvlo on 2009-04-03
I have the same problem... When I'm printing on my HP Deskjet 3420, all pages "shifted up" a little and cutted off there. I have OpenOffice from Jaunty repos.

UPD: mykrob, I've tested your page - "sender" cutted off.

---

### Post by mykrob on 2009-04-03
Well, i get the issue with the OO from the repository or from the direct download from Sun, so OpenOffice is not the issue.


Can someone with a printer other than an HP confirm? Perhaps the hplip driver is the issue, or maybe something in gnome-print.. We need some data from a non-hp printer user to begin to narrow this down so a proper bug report can be filed.

---

### Post by lvlo on 2009-04-03
I have printed simple page in Gedit - it seems fine.

---

### Post by mykrob on 2009-04-03
my regular documents have been fine from openoffice, thus far it has only effected envelopes. Admittedly I haven't done any hardcore testing, I am just trying to work as normal, and if i come across something that goes wrong, we come here.

I have submitted a bug report and referenced this thread, so please continue with your input.

---

### Post by lvlo on 2009-04-04
Please give me a link to bug report :)

---

### Post by mdurham on 2009-04-04
It doesn't even work correctly if printed to a file. Does save on paper though!
Cheers, Mike

---

### Post by bennachie on 2009-04-04
The test document prints perfectly on both my Brother 2140 and my HP 2280.

---

### Post by mykrob on 2009-04-04
Bug Report Link

[https://bugs.launchpad.net/bugs/354915](https://bugs.launchpad.net/bugs/354915)

---

### Post by mykrob on 2009-04-06
any updates here?

---

### Post by mykrob on 2009-04-08
bump..

Ran all updates, setup the printer again, same problem..

If any one at al is experiencing this, PLEASE post here and to the bug report!

---

### Post by tgyorgyi on 2009-04-19
> **mykrob said:**
> 

If any one at al is experiencing this, PLEASE post here and to the bug report!

I have HP3650 deskjet, test page and anything on a regular A4 prints fine from OO or Opera or whatever. However, A5 is absolutely wrong: printing starts only from the middle of the page. This worked fine up until some days ago when I updated to Jaunty RC from Intrepid.

---

### Post by mykrob on 2009-04-20
please add your experience to the bug report

---

### Post by tgyorgyi on 2009-04-22
I did.
Also, I found [this bug]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/357732").

Out of curiousity I changed etc/papersize to A5, and there! A5 printed nicely first time since updating. There is a bugfix on that page too, I will take a look, as changing /etc/papersize every time I want to print non-A4 seems to be a bit of a bother.

EDIT: The bugfix provided at the Lanuchpad link in this post fixed my problem. According to the bug report page sizes that were not the default were not communicated, so for people who have 'letter' in their /etc/papersize the printer would always try letter, and so on.

---


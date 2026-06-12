---
title: "Thunderbird can't authenticate gmail in 17.04, but 16.04.2.LTS works fine"
date: 2017-05-11
forum: Installation &amp; Upgrades
---

### Post by justen_m on 2017-05-11
I am trying to set up thunderbird to access my gmail account. I've done this dozens of times on 14.04-16.04LTS. On my 17.04 machines, two clean installs, I get an... error? I enter all my info, username, passwd, etc. Works fine for my non-gmail accounts, using smtp. Gmail accounts pop up an additional authentication window. The window is non-responsive. I enter my username, click next. Nothing happens. Every link on the pop-up-window is non-responsive.
I configure this the exact same way with 16.04.2LTS and Win10, and it all works. 17.04 doesn't work. The authentication windows are just... dead. I can access my gmail using the web interface... but only brain-hungry alien zombies use web interfaces to access email. I am not dead yet! Help!

I don't think it is just a UI issue. I accessed one of the machines via xrdp/xfce, launched thunderbird, and got the same error.

---

### Post by ajgreeny on 2017-05-11
Same problem here, having just tried in my VBox installation of Ubuntu-Gnome 17.04.

I normally use 16.04, and have been using gmail for many years without a problem on many machines.
The main one uses T'Bird and pop3 still, but I can also login using webmail in a browser without a problem, and I use IMAP on other machines such as an old netbook, also running 16.04 (Lubuntu).

I know that I am using the correct username and password in the setup configuration of the 17.04 version, but I get to the box which says to click on the **Next** button, and it does not move forward from there.
When I get time I shall try installing sylpheed and see if that can manage; it is what I use on most of my other machines where I just check the email server but don't use them for much other than that.

---

### Post by jeremy31 on 2017-05-11
[https://bugzilla.mozilla.org/show_bug.cgi?id=1364006](https://bugzilla.mozilla.org/show_bug.cgi?id=1364006)

Does this fix the issue?

---

### Post by howefield on 2017-05-11
Yep, selecting "Manual config" and then "Normal Password" under the Authentication method drop down does it for me.

---

### Post by ajgreeny on 2017-05-11
Yes, same here.

After my post #2 I searched and found the same info, and have now had a chance to check and all seems well again.

---

### Post by tokumei-74 on 2017-05-11
I always had problems with non-LTS versions of Ubuntu so I stick with LTS releases, 16.04 is starting to get old (soon Debian stable will be more up-to-date than Ubuntu "stable") but still the best option.

---

### Post by Marc_Hoppe on 2017-05-11
Does anyone know when Thunderbird 52.1.0 will be provided in the Update Repository ?

---

### Post by howefield on 2017-05-12
> **Marc_Hoppe said:**
> Does anyone know when Thunderbird 52.1.0 will be provided in the Update Repository ?

Not with any certainty, largely depends on the maintainer. Probably a few days but could be a few weeks.

The good news is that the fix for google Oauth setup which is the subject of this thread seems to be fixed with the new version.

---

### Post by Marc_Hoppe on 2017-05-13
Thanks, who is the "maintainer" ?  Canonical ? Is it correct to say they must first provide the update then distros like Linux Mint will then have to add it as well ? Thunderbird 52.1.0 was released on April 30.

---

### Post by howefield on 2017-05-13
> **Marc_Hoppe said:**
> Thanks, who is the "maintainer" ?  Canonical ? Is it correct to say they must first provide the update then distros like Linux Mint will then have to add it as well ? Thunderbird 52.1.0 was released on April 30.

Details of the package here : [http://packages.ubuntu.com/zesty/thunderbird](http://packages.ubuntu.com/zesty/thunderbird)

---

### Post by Marc_Hoppe on 2017-05-13
Thank you for your response but I see no mention of Thunderbird version 52.1.0 which is the version that fixes the issue mentioned in this thread, This issue also occurred with Tbird in Windows and was fixed by updating to the latest version. So the question is when will Thunderbird 52.1.0 be available in the official Software Repository ? :)

---

### Post by howefield on 2017-05-13
> **Marc_Hoppe said:**
> Thank you for your response but I see no mention of Thunderbird version 52.1.0 which is the version that fixes the issue mentioned in this thread, This issue also occurred with Tbird in Windows and was fixed by updating to the latest version.

I was giving you the answer  to your "*who is the "maintainer" ? Canonical*" question. 

> So the question is when will Thunderbird 52.1.0 be available in the official Software Repository ? :)

Believe I already mentioned that no one here really knows the exact date and time of day the update will be available. You could ask the maintainer(s) although that probably won't make it happen any quicker :)

---

### Post by vasa1 on 2017-05-13
> **Marc_Hoppe said:**
> ... So the question is when will Thunderbird 52.1.0 be available in the official Software Repository ? :)

No idea but look at [https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa)

---

### Post by #&amp;thj^% on 2017-05-13
> **vasa1 said:**
> No idea but look at [https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa)

+1 :)
If your not oposed to adding a PPA...you will see it in:
```
thunderbird-mozilla-build/stable 52.1.0-0ubuntu1 amd64
  Mozilla Thunderbird, official Mozilla build, packaged for Ubuntu by the Ubuntuzilla project.

```
I have used the PPA for a few years now...so I have no trust issues here.

[https://www.ubuntuupdates.org/ppa/ubuntuzilla](https://www.ubuntuupdates.org/ppa/ubuntuzilla)

---

### Post by Marc_Hoppe on 2017-05-13
> **howefield said:**
> 
Believe I already mentioned that no one here really knows the exact date and time of day the update will be available. You could ask the maintainer(s) although that probably won't make it happen any quicker :)

My question was aimed at the "maintainers". I'm not sure if they or their representatives follow this forum. I belong to several non-Linux related forums where the developers are active so it's not totally unheard of that the people who write the code take feedback from the user base in a Forum.  I haven't been a member of this forum long enough to know who is or is not involved. :)

---

### Post by Marc_Hoppe on 2017-05-13
> **1fallen said:**
> +1 :)
If your not oposed to adding a PPA...you will see it in:
```
thunderbird-mozilla-build/stable 52.1.0-0ubuntu1 amd64
  Mozilla Thunderbird, official Mozilla build, packaged for Ubuntu by the Ubuntuzilla project.

```
I have used the PPA for a few years now...so I have no trust issues here.

[https://www.ubuntuupdates.org/ppa/ubuntuzilla](https://www.ubuntuupdates.org/ppa/ubuntuzilla)

Thanks I might try adding the PPA or I might just wait for the official release of 52.1.0 since I can check Gmail on my Windows computers.:D

---

### Post by howefield on 2017-05-17
New version of Thunderbird now available in the repository.

```
apt-cache policy thunderbird
thunderbird:
  Installed: (none)
  Candidate: 1:52.1.1+build1-0ubuntu0.17.04.1
  Version table:
     1:52.1.1+build1-0ubuntu0.17.04.1 500
        500 http://gb.archive.ubuntu.com/ubuntu zesty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu zesty-security/main amd64 Packages
     1:45.8.0+build1-0ubuntu1 500
        500 http://gb.archive.ubuntu.com/ubuntu zesty/main amd64 Packages
```

---


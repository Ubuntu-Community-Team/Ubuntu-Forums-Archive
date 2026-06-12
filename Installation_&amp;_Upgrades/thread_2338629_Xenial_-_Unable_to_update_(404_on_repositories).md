---
title: "Xenial - Unable to update (404 on repositories)"
date: 2016-09-30
forum: Installation &amp; Upgrades
---

### Post by connormacrae141747 on 2016-09-30
Hi all,

I have been using the new LTS for ubuntu for a good few months now, but have suddenly starting coming across a truly strange issue whereby I cannot update or install new software from repositories.  First off when trying to run software updater I am hit with the error of 'Failed to download repository information - check your internet connection', and then when trying to run:

```
>sudo apt-get clean
>sudo apt-get upgrade
>sudo apt-get update
```

I recieve this output (bereft with 404's):

```
macracon@Macracon-HP-ENVY:/usr/lib$ sudo apt-get clean
macracon@Macracon-HP-ENVY:/usr/lib$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-34 linux-headers-4.4.0-34-generic linux-image-4.4.0-34-generic
  linux-image-extra-4.4.0-34-generic linux-signed-image-4.4.0-34-generic
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
macracon@Macracon-HP-ENVY:/usr/lib$ sudo apt-get update
Err:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease
  Temporary failure resolving 'gb.archive.ubuntu.com'
Err:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates InRelease
  Temporary failure resolving 'gb.archive.ubuntu.com'
Err:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports InRelease
  Temporary failure resolving 'gb.archive.ubuntu.com'
Err:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security InRelease
  Temporary failure resolving 'gb.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://gb.archive.ubuntu.com/ubuntu/dists/xenial/InRelease)  Temporary failure resolving 'gb.archive.ubuntu.com'
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease](http://gb.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease)  Temporary failure resolving 'gb.archive.ubuntu.com'
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease](http://gb.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease)  Temporary failure resolving 'gb.archive.ubuntu.com'
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/xenial-security/InRelease](http://gb.archive.ubuntu.com/ubuntu/dists/xenial-security/InRelease)  Temporary failure resolving 'gb.archive.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.
macracon@Macracon-HP-ENVY:/usr/lib$ 
```

Now, my internet connection is working for all other programs, and in addition modifying my resolv.conf to change DNS does not help (for example added 8.8.8.8 and 8.8.4.4).  Furthermore, changing repository server from GB to main server does not help either.  I am lost as to what else to try and resolve this problem (and a clean install would be a huge headache).  Any help will be hugely appreciated!

---

### Post by howefield on 2016-09-30
Are you using a proxy server ?

---

### Post by connormacrae141747 on 2016-09-30
Nope I am not - I have also tried with setting proxy to automatic which didn't make a difference.

---

### Post by connormacrae141747 on 2016-09-30
I should say I am currently working through a University connection - but this does occur when on other networks too.

---

### Post by ian-weisser on 2016-09-30
Those archives do exist, and are reachable when I try.
The type or problem you describe (happens only to apt, happens on somebody-elses-large-network) are classic symptoms of a proxy on that large network. [Solution for that]("https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy").

---

### Post by connormacrae141747 on 2016-09-30
Okay thank you for that - I will try that and also (when I get home) try on home network to confirm whether or not the issue is still present.

I will update afterwards.

Thanks!

---

### Post by connormacrae141747 on 2016-10-02
UPDATE:

So after once again attempting to update at home on my personal network I encounter all of the same issues as described in my original post - So I don't see how the issue can be because of a proxy on a large network (which it might have been at the university I work at). 

Does anyone have any other possible solutions to this?

---

### Post by ian-weisser on 2016-10-03
Connections to the the Ubuntu Repositories (and mirrors) use ordinary http connections.
Pick a failed connection and try that URL using a web browser.

Example:
```
Hit:11 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease

URL: http://us.archive.ubuntu.com/ubuntu/dists/xenial-backports/
```
See the pattern?

If you CANNOT connect using a web browser, then the problem is your internet connection. There are steps to take to narrow that down to a cause.

If you CAN connect using a web browser, then you have broken apt settings. There are different steps to take to fix it.

Which path do you need to go down?

---

### Post by connormacrae141747 on 2016-10-03
I was able to access all of the URLs that were 'temporarily unavailable' in browser, as well as ping them, so it was not an issue with connection.

However - After much annoyance I have gone ahead and reinstalled to hit reset on this issue (there were a few other issues present as well that led to this decision).  Therefore, everything is now working as expected.  Hopefully, this issue does not occur again!

Thanks for all the suggestions though.

---


---
title: "ubuntu update manager 10.10 flash/firefox fails"
date: 2011-07-05
forum: Installation &amp; Upgrades
---

### Post by bebopiiam on 2011-07-05
Hi all.  A couple of weeks ago update manager started to fail for the flash installer.  Now it's also failing on firefox updates.

Here are the errors I'm getting:
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_3.6.18+build2+nobinonly-0ubuntu0.10.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_3.6.18+build2+nobinonly-0ubuntu0.10.10.1_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-branding_3.6.18+build2+nobinonly-0ubuntu0.10.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-branding_3.6.18+build2+nobinonly-0ubuntu0.10.10.1_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_3.6.18+build2+nobinonly-0ubuntu0.10.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_3.6.18+build2+nobinonly-0ubuntu0.10.10.1_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.3.181.26ubuntu0.10.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.3.181.26ubuntu0.10.10.1_i386.deb) 404  Not Found [IP: 91.189.92.167 80]

I'm not finding anyone else with this problem and every thing else has been updating fine.  Anyone have any ideas??

Thanks
Steve S.:(

BTW -- this is an Acer Aspire One netbook.

---

### Post by youngmj on 2011-07-07
> I'm not finding anyone else with this problem.

I have been seeing these 404 errors, too.  I just decided to look online to see if any resolution has been found when I came across this thread.  Still looking for a solution...

Error messages shown below:
****************************************

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_3.6.18+build2+nobinonly-0ubuntu0.10.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_3.6.18+build2+nobinonly-0ubuntu0.10.04.1_i386.deb)
  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-branding_3.6.18+build2+nobinonly-0ubuntu0.10.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-branding_3.6.18+build2+nobinonly-0ubuntu0.10.04.1_i386.deb)
  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_3.6.18+build2+nobinonly-0ubuntu0.10.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_3.6.18+build2+nobinonly-0ubuntu0.10.04.1_i386.deb)
  404  Not Found [IP: 91.189.92.166 80]

---

### Post by spikoley on 2011-07-09
I think I have this same issue with the updates to 10.10.  Flash does not work in Firefox.  When I did the updates it gave me an error and now Flash doesn't work.

Any ideas?

---

### Post by bebopiiam on 2011-07-13
I started to say 'SOLVED' but I have no idea why things are working now.  I guess someone fixed the repositories or something...  All my problem updates downloaded and installed ok.  Firefox is still working and so is Flash.  Whoever the angel is out there -- Thanks :)

Steve S.

---


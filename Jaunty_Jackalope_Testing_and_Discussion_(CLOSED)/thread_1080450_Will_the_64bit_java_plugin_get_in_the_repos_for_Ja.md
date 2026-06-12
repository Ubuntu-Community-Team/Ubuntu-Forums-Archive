---
title: "Will the 64bit java plugin get in the repos for Jaunty."
date: 2009-02-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-02-25
It's working a treat on Intrepid. Even though it's beta.

---

### Post by taavikko on 2009-02-25
It's already in and in use...

> Date: Fri, 06 Feb 2009 14:50:33 -0000
From: Matthias Klose <doko@ubuntu.com>
Subject: [ubuntu/jaunty] sun-java6 6-12-0ubuntu1 (Accepted)
To: [email]jaunty-changes@lists.ubuntu.com[/email]
Message-ID:
       <20090206145033.15101.81330.launchpad@cocoplum.canonical.com>
Content-Type: text/plain; charset="utf-8"

sun-java6 (6-12-0ubuntu1) jaunty; urgency=low

 * New upstream release. Closes: #508195, #507979.
   Release notes at [http://java.sun.com/javase/6/webnotes/ReleaseNotes.html](http://java.sun.com/javase/6/webnotes/ReleaseNotes.html).
 * Build the -plugin package on amd64. Closes: #508871.
 * Install desktop files for javaws and the plugin control panel on amd64.
 * Find the correct doc zip when installing the -doc package. LP: #85969.
   LP: #321863.

---

### Post by philinux on 2009-02-25
Rebooting to Jaunty.....

---

### Post by philinux on 2009-02-25
Right I've uninstalled the iceatea plugin and now using the sun-java6-plugin.

Testing again...

---

### Post by KhaaL on 2009-02-25
is it in the repos as sun-java6, the native 64bit plugin?

---

### Post by kurros on 2009-02-25
> **KhaaL said:**
> is it in the repos as sun-java6, the native 64bit plugin?

Yes its part of sun-java6

> 
$ dpkg --search /usr/lib/jvm/java-6-sun-1.6.0.12/jre/lib/amd64/libnpjp2.so
sun-java6-bin: /usr/lib/jvm/java-6-sun-1.6.0.12/jre/lib/amd64/libnpjp2.so


sun-java6-plugin installs the necessary update-alternatives/mozilla symlinks.

---


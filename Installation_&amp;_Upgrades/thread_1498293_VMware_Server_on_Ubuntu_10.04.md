---
title: "VMware Server on Ubuntu 10.04"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by SirEddy on 2010-05-31
G'day all,


I have just loaded Ubuntu 10.0.4 all OK


Loaded VMware Server 2.0.2 All OK

Opened VMware Infrastructure Web page and created new machine.  Still OK

Click on new machine and go to console and power on.

Receive error:


Cannot access virtual machine console. Request timed out.
The attempt to acquire valid session ticket for "xxxxxx" took longer than expected.  If this problem persists blah blah blah

I suspect this is a problem with Mozilla Firefox 3.6.3.

Does anybody have any ideas.

Interesting?

---

### Post by useResa on 2010-06-02
I have ran into the same issue as indicated. From what I have read it is indeed an issue with Firefox 3.6.3. I have used the following to circumvent the issue:

First I have downloaded Firefox 3.5.9 from [here]("http://www.mozilla.com/en-US/firefox/all-older.html").
I extracted the tarball in the folder where I had downloaded the file and renamed the folder from firefox to firefox-3.5.9
Next I moved the entire folder to the /usr/lib directory (you should now have a firefox-3.6.3 and a firefox-3.5.9 directory).
Then created a symbolic link in the /usr/bin directory with the following command
```
ln -s /usr/lib/firefox-3.5.9/firefox firefox-old
```
Now I can choose to start the regular firefox version (with the command *firefox*) and the old release with the command *firefox-old*.
Next I uninstalled the console plugin (if you have not yet done so), started the old firefox version, logged into vmware and installed the console plugin into the old version.
In this release of firefox I can now use the console as I was used to.

I hope this helps.

---

### Post by anjoze on 2010-06-22
Hi. I followed your steps, create the symbolic link (firefox-old -> /usr/lib/firefox-3.5.9/firefox) but when I write "firefox-old" says: command not found.
Help please...
Thanks

---

### Post by useResa on 2010-06-22
Have you created the symbolic link while you were in the /usr/bin directory?
Just to be sure, could you post the outcome of the following command
```
ls -l /usr/bin/firef*
```

---

### Post by fmartagong on 2010-07-08
> **useResa said:**
> I have ran into the same issue as indicated. From what I have read it is indeed an issue with Firefox 3.6.3. I have used the following to circumvent the issue:

First I have downloaded Firefox 3.5.9 from [here]("http://www.mozilla.com/en-US/firefox/all-older.html").
I extracted the tarball in the folder where I had downloaded the file and renamed the folder from firefox to firefox-3.5.9
Next I moved the entire folder to the /usr/lib directory (you should now have a firefox-3.6.3 and a firefox-3.5.9 directory).
Then created a symbolic link in the /usr/bin directory with the following command
```
ln -s /usr/lib/firefox-3.5.9/firefox firefox-old
```Now I can choose to start the regular firefox version (with the command *firefox*) and the old release with the command *firefox-old*.
Next I uninstalled the console plugin (if you have not yet done so), started the old firefox version, logged into vmware and installed the console plugin into the old version.
In this release of firefox I can now use the console as I was used to.

I hope this helps.

I really helped this.

Thank you very much.

---

### Post by arendi on 2010-07-26
The way we solved this problem (in short) is that we downloaded firefox 3.5.11 (the last of the 3.5 series i think), started it, logged in vmware server via default web interface, then we generated desktop shortcuts for all virtual machines (backed shortcuts up just in case of accidental deletions) and then removed firefox 3.5.11. So now we have up-to-date Firefox AND access to all virtual machines.

Strange, the problem was only in starting the console from within  the firefox 3.6.x, because other managing via VMware Server Web Interface works almost fine (session dies sometimes without reason). I don't think this bug requires much work to fix, but for 6 months, neither VMware nor Mozilla have fixed it, and I don't think they will do it any time soon.

---

### Post by santan on 2010-10-31
> **useResa said:**
> I have ran into the same issue as indicated. From what I have read it is indeed an issue with Firefox 3.6.3. I have used the following to circumvent the issue:

First I have downloaded Firefox 3.5.9 from [here]("http://www.mozilla.com/en-US/firefox/all-older.html").
I extracted the tarball in the folder where I had downloaded the file and renamed the folder from firefox to firefox-3.5.9
Next I moved the entire folder to the /usr/lib directory (you should now have a firefox-3.6.3 and a firefox-3.5.9 directory).
Then created a symbolic link in the /usr/bin directory with the following command
```
ln -s /usr/lib/firefox-3.5.9/firefox firefox-old
```Now I can choose to start the regular firefox version (with the command *firefox*) and the old release with the command *firefox-old*.
Next I uninstalled the console plugin (if you have not yet done so), started the old firefox version, logged into vmware and installed the console plugin into the old version.
In this release of firefox I can now use the console as I was used to.

I hope this helps.


Thanks so much Bud. It really helped!!!

---

### Post by stevellion on 2011-03-12
I have it working on Firefox 3.6.15 with no problems now.  The following steps were required.

1) Manually install the plugin
    cd /usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16/webapps/ui/plugin
    ls     Just to ensure that you see the various .xpi files for the plugins.
    firefox vmware-vmrc-linux-x64.xpi  (or whichever version is relevant for you)

2) Enable ssl2 in Firefox.
    in Firefox, go to about:config
    Find security.enable_ssl2 and set it to true

Try your VMware Server link - Hey presto.

---

### Post by saxophobe on 2011-03-16
I know this is probably an idiotic question, but what is the command to manually install .xpi files?

---

### Post by saxophobe on 2011-03-16
Nevermind.  I figured it out.  8-)

---


---
title: "Strange firefox / ssh behaviour"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Shootfast on 2009-04-09
Howdy folks,

I've been using the Jaunty x86_64 alpha (now beta) for a while and noticed some peculiarity when using firefox over ssh.

I have a small server running Hardy x86_64 and Vmware server. When I couldn't remember the address for the Virtual Infrastructure web access I figured I'd just shell in and run "vmware". 
The expected behavior was that firefox would launch on my hardy server and it's X session would be forwarded to my own Jaunty box (I can tell which is which by the GTK themes not matching). I have done this on intrepid many times.

On Jaunty, after I ssh -X into my hardy server and run "vmware" (which just starts firefox at the vmware address) The local copy of firefox suddenly got a new tab with the new page in it.
As cool as this was (the remote firefox mingling with my local firefox) This was not the intended behaviour, and indeed just having an X forwarded shell open means that If I launch firefox from anywhere on my local machine when it isn't already running, it starts from the remote box and forwards over! (The themes don't match and my homepage is different!)

Is this a new *feature*? I didn't want to file a bug report in case this was the expected result, but it's definitely not what it used to be!

Local: OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
Remote: OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007

---


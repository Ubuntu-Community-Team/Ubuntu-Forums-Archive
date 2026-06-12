---
title: "need help with pidgin on HP mini 1000"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by icesparrow on 2009-12-27
Hi, 
I bought an HP mini 1000 and recently found out that Pidgin msn no longer works due to server protocol change. So I tried to upgrade with update manager. I went to the pidgin's website and did the following:
 
 
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \ 67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \ `lsb_release --short --codename` main | \
sudo tee /etc/apt/sources.list.d/pidgin-ppa.list
 
I changed $DISTRO_CODENAME to "hardy" so lsb_release --short --codename comes out to be "hardy". HP originally did not set distro codename to anything, but a post in the archived forum said it is actually hardy. But after I ran the upgrade manager, all it did was uninstall my existing outdated pidgin. So now I have no pidgin, and upgrade manager doesn't cover pidgin under the "internet" category. Only Skype 2 shows up in there. Can anybody help with that? If somebody had already encoutered the same problem and posted a solution somwhere, plz give me the link. Thanks in advance.

---

### Post by sliketymo on 2009-12-27
run: sudo "apt-get install pidgin" in a terminal.I have been using pidgin with msn for years with no problems.

---

### Post by icesparrow on 2009-12-27
tried sudo 'apt-get install pidgin'   error: sudo: apt-get install pidgin: command not found

very very weird. Please help, thanks

---

### Post by wekebu on 2009-12-29
For the past 2 weeks?, I've been getting, Our protocol is not supported by the server.  Previous to this, Pidgin had worked for years...

Edit:  I installed Kopete and it didn't work; at first.  Then I opened my browser and went directly to my instant messenger 'provider', which is MSN and got a error that my browser wasn't accepting third party cookies, which was correct.  I changed that, still not working, but noticed that Firefox was automatically login with my previous email address.  Logged in using the correct MSN id, and now Kopete works.  I still can't get Pidgin to work.  This is an alternative for now until I find more time to figure it out.

---


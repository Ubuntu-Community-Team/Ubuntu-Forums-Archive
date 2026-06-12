---
title: "software updater offers 15.10 from 14.04"
date: 2016-04-21
forum: Installation &amp; Upgrades
---

### Post by recurringvisitor on 2016-04-21
So, here's what I've got. I've been using 14.04 LTS for a while now but would like to upgrade to 16.04. I have software updates checked for any new version and when checking I am offered version 15.10 but nothing else. My intent is installing 16.04, not 15.10. How can I go about doing that? Should I upgrade to 15.10 directly from 14.04 and then hopefully to 16.04 LTS? Any help on this appreciated.

---

### Post by Bashing-om on 2016-04-21
recurringvisitor; Hello;

No can do from GUI just yet.
> 
Users of 14.04 LTS will be offered the automatic upgrade when 16.04.1 LTS is released, which is scheduled for July 21st.


What you can do is from terminal IF you are fully updated, no proprietary drivers ( and all other software reverted) in use.
```

sudo apt update
sudo apt upgrade
sudo do-release-upgrade -d

```
where the '-d' is (d)evelopment .. which will be in effect UNtil the .1 release .

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2016-04-21
> I have software updates checked for any new version

It should be set for "Long-term support versions" if we want to go from one LTS to the next LTS without going through the Interim releases in between.

Regards.

---

### Post by recurringvisitor on 2016-04-21
Thanks grahammechanical. I already tried that but still all I get is "software is up to date." Look like I will have to go with what Bashing-om advises and either try update from terminal or wait until July.

---

### Post by ajgreeny on 2016-04-21
You will not see the update from 14.04 to 16.04 in the software-centre or updater until we get to the first point release 16.04.1.

This is to allow any bugs that are in the release version to be squashed.  Wait till July (probably) if you want to update using the GUI though you can do it in command-line if you wish before that.

Whoops; I missed Bashing-om's post above, but same content, so your choice.

---

### Post by recurringvisitor on 2016-04-21
Sudo do release-upgrade -d gives me this:

Err Upgrade tool signature                                                     
  404  Not Found [IP: 2001:67c:1562::16 80]                                    
Err Upgrade tool                                                               
  404  Not Found [IP: 2001:67c:1562::16 80]                                    
Fetched 0 B in 0s (0 B/s)                                                      
WARNING:root:file 'utopic.tar.gz.gpg' missing
Failed to fetch
Fetching the upgrade failed. There may be a network problem. 

Seems to be trying to upgrade to utopic 14.10?

Don't know at this point if it's even possible getting from 14.04 to 16.04 unless doing a clean install and I'm really not ready for that.

---

### Post by Bashing-om on 2016-04-21
recurringvisitor; Hey;

In the update manager, have you set the option to upgrade to LTS  ?

We can quickly verify :
```

cat /etc/update-manager/release-upgrades

```
is " Prompt=lts" set ?
Be aware that earlier this day a bug in the upgrade process was found ( hang @15.10 ) that have been fixed .

Also .. insure that there are no outside PPAs in the current install that have no support in 16.04. A PPA is outside the control of ubuntu.

Do we need to check your source lists ?

[INDENT]dot the i's cross the t's
[INDENT][INDENT][INDENT]then jump
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by recurringvisitor on 2016-04-21
Thanks to all, I did it! Now running 16.04 after getting the system up in 15.10 (some minor bumps  like a black screen but managed getting out of it), I'm up and running just fine.

---

### Post by Bashing-om on 2016-04-22
recurringvisitor; Great !

You do good work :)

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---


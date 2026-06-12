---
title: "Bitcoin won't run, ubuntu 11.1"
date: 2012-03-14
forum: Installation &amp; Upgrades
---

### Post by davedaverson on 2012-03-14
Hi everybody,
  I'm enjoying Ubuntu for the most part, definitely teaching me to be patient. So, I have searched high and low and did find some search results for my error but all of the solutions did not work.

I've tried adding the repository without success. When typing sudo add-apt-repository ppa:bitcoin/bitcoin
I get this output
"Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 88, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 80, in get_ppa_info_from_lp
    curl.perform()
pycurl.error: (51, "SSL: certificate subject name (*.opendns.com) does not match target host name 'launchpad.net'")"

When I try and launch bitcoin-qt from command prompt I get "EXCEPTION: 22DbRunRecoveryException       
DbEnv::open: DB_RUNRECOVERY: Fatal error, run database recovery       
bitcoin in Runaway exception       

terminate called after throwing an instance of 'DbRunRecoveryException'
  what():  DbEnv::open: DB_RUNRECOVERY: Fatal error, run database recovery
Aborted"

I have searched the internets, and any solutions do not work. I cannot figure out why I'm getting the flipping DNS error on the PPA update arrggggggggg.

Why has no one else had this problem. This is ridiculously hard to find a solution too, even on the bitcoin wenbsite. PLEASE HELP. I'm about ready to just run this on windows, which I hate the idea of. 

Someone has to be running bitcoin on 11.1.
 
Your frustrated N00b.

---

### Post by otherethe on 2012-03-15
> **davedaverson said:**
> Hi everybody,
  I'm enjoying Ubuntu for the most part, definitely teaching me to be patient. So, I have searched high and low and did find some search results for my error but all of the solutions did not work.

I've tried adding the repository without success. When typing sudo add-apt-repository ppa:bitcoin/bitcoin
I get this output
"Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 88, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 80, in get_ppa_info_from_lp
    curl.perform()
pycurl.error: (51, "SSL: certificate subject name (*.opendns.com) does not match target host name 'launchpad.net'")"

When I try and launch bitcoin-qt from command prompt I get "EXCEPTION: 22DbRunRecoveryException       
DbEnv::open: DB_RUNRECOVERY: Fatal error, run database recovery       
bitcoin in Runaway exception       

terminate called after throwing an instance of 'DbRunRecoveryException'
  what():  DbEnv::open: DB_RUNRECOVERY: Fatal error, run database recovery
Aborted"

I have searched the internets, and any solutions do not work. I cannot figure out why I'm getting the flipping DNS error on the PPA update arrggggggggg.

Why has no one else had this problem. This is ridiculously hard to find a solution too, even on the bitcoin wenbsite. PLEASE HELP. I'm about ready to just run this on windows, which I hate the idea of. 

Someone has to be running bitcoin on 11.1.
 
Your frustrated N00b.

Try this download [http://sourceforge.net/projects/bitcoin/files/Bitcoin/bitcoin-0.5.2/bitcoin-0.5.2-linux.tar.gz/download](http://sourceforge.net/projects/bitcoin/files/Bitcoin/bitcoin-0.5.2/bitcoin-0.5.2-linux.tar.gz/download), goto your /home/*User name/.bitcoin delete all files there but your wallet extract the files of bitcoin-0.5.2  after extract it'll be were you extract/bin/32 or 64 depending on your os,/bitcoin-qt Just dbl click on the bitcoin-qt should work fine for you so long as you deleted the files in .bitcoin

If this helps Donate :) 1HZyWtxnE7WoXeS6T8YmnhUKUX2oP8s3GQ or not doesn't matter I would have helped ether way

---

### Post by davedaverson on 2012-03-16
Thanks for the response, I was able to get to the directory from the CLI. How can I view this in Dolphin? Why can't I see this folder normally? So I guess I need to find out how to delete from the command line but isn't there a way for me to view the files in Dolphin and just delete them manually?


***Side Rant***
Are there any good books out there on Kubuntu so I don't feel like such a retard. I swear to GOD, everything is 20000000000000000 times harder in Kubuntu. My wireless randomly stops working but that's a whole other issue. Then I have to search online where everyone has a had a similar issue but the resolution has nothing to do with my problem and on top of it all the posts were from 2007 and another version of kubuntu.

How exactly is Kubuntu more stable? just saying, cuz everything is broken almost all the time.

---

### Post by john_spiral on 2012-05-16
Just rename .bitcoin, re-run app, should come up.

---


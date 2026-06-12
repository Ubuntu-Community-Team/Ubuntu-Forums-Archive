---
title: "winbindd: Could not fetch our SID - did we join?"
date: 2010-01-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gmoore777 on 2010-01-26
LucidLynx Alpha2+, 64bit 2.6.32-11-generic and
Using the newer likewise-open 5.4.0.39949-3

I can successfully add the linux machine to the ActiveDirectory domain
such that i can log in as DOMAIN\\first.last.

But I do not see any winbind processes nor samba processes
and these commands, as expected, are not successful:

    $ wbinfo -p
    Ping to winbindd failed
    could not ping winbindd!

    $ wbinfo -t
    checking the trust secret via RPC calls failed
    Could not check secret


When I start up winbind via `sudo /etc/init.d/winbind restart`: 
 I get in /var/log/samba/log.winbindd the following:

[2010/01/26 15:19:23,  0] winbindd/winbindd_cache.c:2578(initialize_winbindd_cache)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2010/01/26 15:19:23,  0] winbindd/winbindd_util.c:782(init_domain_list)
  Could not fetch our SID - did we join?
[2010/01/26 15:19:23,  0] winbindd/winbindd.c:1393(main)
  unable to initialize domain list


So, has anyone got likewise-open running on LucidLynx, and then
in addition, have successful winbindd processes running?
and have successful `wbinfo -t`, `wbinfo -p`, etc.


(I have had this running on HardyHeron 32 bit for the last 2 years on
dozens of machines (and most recently on a couple of 64 bit machines). Having said that, I could have done something stupid.)

---

### Post by gmoore777 on 2010-02-13
I still could use some winbind help.
I have the same error, and still have the latest and greatest LucidLynx packages installed.

Anyone know how I can get winbindd to give me a bit more information on what it is trying to do at the time that it craps out with:

[2010/01/26 15:19:23, 0] winbindd/winbindd_cache.c:2578(initialize_winbindd_cache)
initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2010/01/26 15:19:23, 0] winbindd/winbindd_util.c:782(init_domain_list)
Could not fetch our SID - did we join?
[2010/01/26 15:19:23, 0] winbindd/winbindd.c:1393(main)
unable to initialize domain list

---


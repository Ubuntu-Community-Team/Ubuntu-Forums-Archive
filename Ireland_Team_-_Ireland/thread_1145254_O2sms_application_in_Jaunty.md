---
title: "O2sms application in Jaunty"
date: 2009-05-01
forum: Ireland Team - Ireland
---

### Post by tck on 2009-05-01
Having issues with this since upgrading/installing... anyone else having difficulties? ([http://o2sms.sourceforge.net/](http://o2sms.sourceforge.net/))

> 
[ logging in to [email]086XXXXXXX@o2.ie[/email] ... ]
ERROR: STEP2: Unexpected failure in step 2 (subtype submit_form); can't find the form 'dashboard-login-form'
Can't store CODE items at ../../lib/Storable.pm (autosplit into ../../lib/auto/Storable/_store.al) line 264, <STDIN> line 2, at /usr/share/perl5/WWW/SMS/IE/iesms.pm line 1010


---

### Post by matze_ on 2009-05-01
The o2 website has changed. o2sms doesnt work atm.

---

### Post by tck on 2009-05-03
coolio!

---

### Post by matze_ on 2009-05-07
it's working again with todays update.

---

### Post by mickyjo on 2009-05-08
I still get the following error:
```
$ o2sms --version
/usr/bin/o2sms version 3.33
(Getopt::Long::GetOptions version 2.37; Perl version 5.10.0)
``````
$o2sms -C vodafone -u 08xxxxxxxx -p xxxx -m "test message" 087xxxxxxx
[ recipient : +35387xxxxxxx ]
[ logging in to 0xxxxxxxx@vodafone.ie ... ]
Can't store CODE items at ../../lib/Storable.pm (autosplit into ../../lib/auto/Storable/_store.al) line 264, at /usr/share/perl5/WWW/SMS/IE/iesms.pm line 1010

```anyone any advice?, this is on ubuntu jaunty
```
$uname -a
Linux xps 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
```

---

### Post by mcdavey on 2009-07-04
Add the following line to the file "iesms.pm" just after the line that says "use constant TG4W_QUIET => 0":

         $Storable::forgive_me = 1;

It doesn't kill the error message, but the text sending should all work fine.  If you really want to kill the error message you could add the following lines instead (but I believe this could introduce a slight security risk):

        $Storable::Deparse = 1;
        $Storable::Eval = 1;

---

### Post by mcdavey on 2009-07-04
That 'smiley' in my previous message should be colon-D
That is, it should read "$Storable::" followed by "Deparse = 1;"

---

### Post by oscarBravo on 2009-07-15
> **mcdavey said:**
> That 'smiley' in my previous message should be colon-D
That is, it should read "$Storable::" followed by "Deparse = 1;"

I've tried both approaches, and still having a problem: ```
paul@vila:~$ vodasms 087xxxxxxx
[ recipient : +35387xxxxxxx ]
test
[ reusing last login for 087xxxxxxx@vodafone.ie ... ]
[ sending message after 10 seconds ... ]
WARNING: STEP7: skipping assert-text-exists action; no previous request
ERROR: STEP8: No previous request
[ message sending failed; No previous request ]
[ Retry ? y/n [n] : ] n
[ okay, I'm outta here ] 
``` Any ideas?

---

### Post by der_ on 2009-08-05
> **oscarBravo said:**
> I've tried both approaches, and still having a problem: ```
paul@vila:~$ vodasms 087xxxxxxx
[ recipient : +35387xxxxxxx ]
test
[ reusing last login for 087xxxxxxx@vodafone.ie ... ]
[ sending message after 10 seconds ... ]
WARNING: STEP7: skipping assert-text-exists action; no previous request
ERROR: STEP8: No previous request
[ message sending failed; No previous request ]
[ Retry ? y/n [n] : ] n
[ okay, I'm outta here ] 
``` Any ideas?

I just added $Storable::forgive_me = 1; and got the same error. I deleted ~/.vodasms/.cookie and it worked afterwards:

```
$ vodasms me
[ recipient : me (+3538xxxxxxxx) ]
test
.
[ logging in to 08xxxxxxxx@vodafone.ie ... ]
Can't store item CODE(0x9127800) at ../../lib/Storable.pm (autosplit into ../../lib/auto/Storable/_store.al) line 264, <STDIN> line 2.
Can't store item CODE(0x8bb67a0) at ../../lib/Storable.pm (autosplit into ../../lib/auto/Storable/_store.al) line 264, <STDIN> line 2.
[ login successful ]
[ sending message after 10 seconds ... ]
Can't store item CODE(0x9127800) at ../../lib/Storable.pm (autosplit into ../../lib/auto/Storable/_store.al) line 264.
Can't store item CODE(0x8bb67a0) at ../../lib/Storable.pm (autosplit into ../../lib/auto/Storable/_store.al) line 264.
[ message sent to +3538xxxxxxxx, 285 remaining this month ]

```

---

### Post by brk3 on 2009-08-20
Hi, can I just get a bump in here, has anyone noticed that meteor support is broken?  They did a weekend of maintenance on the site about a fortnight ago and it's been broken since.

I've left a message on the sourceforge project page but no response.  Anyone have any ideas or the same problem?

xxx@xxx-desktop:~$ o2sms -u xxxx -p xxxx -C meteor xxxx
[ recipient : +xxxx ]
asdf
.
[ logging in to [email]xxxx@meteor.ie[/email] ... ]
[ login failed; Assertion failed in step 6 (assert-text-exists): no match for "MyMeteor Overview" ]
[I]
Edit:
I've managed to fix the above bug myself.  Have emailed the author but no word at the moment about him updating it.  If anyone needs the fix just email me.[/I]

---

### Post by AndrewMc on 2009-08-25
> **brk3 said:**
> Edit:
I've managed to fix the above bug myself.  Have emailed the author but no word at the moment about him updating it.  If anyone needs the fix just email me.

New version (3.34) yesterday apparently fixes meteor support.

---

### Post by tck on 2010-03-03
Anyone running o2sms in Lucid Lynx Alpha 3 ?

when I run it.. I get this response

```

tux@akira:~$ sudo o2sms 
Error in option spec: "history|h|"

```

---

### Post by brk3 on 2010-05-02
> **tck said:**
> Anyone running o2sms in Lucid Lynx Alpha 3 ?

when I run it.. I get this response

```

tux@akira:~$ sudo o2sms 
Error in option spec: "history|h|"

```

Same problem here :/

Edit: latest version from svn seems to fix this, working fine now.

---


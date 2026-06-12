---
title: "Apache / PHP Segfaults"
date: 2009-08-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by fifth on 2009-08-23
I've been having problems with a site I'm working on in Karmic. The problem is very random. Testing the site on localhost the pages will load correctly approx 19/20 times. But occasionaly firefox will prompt to download the php file. Downloading and checking the file shows its empty.

Chrome shows similar problems but gives a message;

```
Error 324 (net::ERR_EMPTY_RESPONSE): Unknown error.
```

Checking the apache error logs shows ;
```

[Sun Aug 23 19:59:29 2009] [notice] Apache/2.2.12 (Ubuntu) PHP/5.2.10-2ubuntu2 with Suhosin-Patch configured -- resuming normal operations     
[Sun Aug 23 20:00:15 2009] [notice] child pid 17481 exit signal Segmentation fault (11)                                                        
[Sun Aug 23 20:00:34 2009] [notice] child pid 17483 exit signal Segmentation fault (11)                                                        
[Sun Aug 23 20:00:34 2009] [notice] child pid 17484 exit signal Segmentation fault (11)                                                        
[Sun Aug 23 20:00:35 2009] [notice] child pid 17488 exit signal Segmentation fault (11)                                                        
[Sun Aug 23 20:00:36 2009] [notice] child pid 17480 exit signal Segmentation fault (11)                                                        
[Sun Aug 23 20:12:54 2009] [notice] child pid 17491 exit signal Segmentation fault (11)                                                        
[Sun Aug 23 20:12:55 2009] [notice] child pid 17493 exit signal Segmentation fault (11)                                                        
[Sun Aug 23 20:12:55 2009] [notice] child pid 17496 exit signal Segmentation fault (11)                                                        
[Sun Aug 23 20:12:56 2009] [notice] child pid 17482 exit signal Segmentation fault (11)  

```

The problem seems to appear when my php code uses start_session(). The code I've been testing with is;

```

<?php

    session_start();
    if(isset($_SESSION['views']))
        $_SESSION['views'] = $_SESSION['views']+ 1;
    else
        $_SESSION['views'] = 1
        
?>
<html>
    <head>
        <title>Test Page</title>
    </head>
    <body>
        <h1>Session Test</h1>
        <p>
            Page been viewed <?php echo $_SESSION['views']; ?>.
        </p>
    </body>
</html>

```

I'm hoping this is just a Karmic problem and not a problem with my code :/ But I'm at a loss to diagnose the problem.

---

### Post by nick_stokie on 2009-08-23
+1

I'm getting exactly the same errors. At first mine was only about 15/20 success rate. I, too, am using session_start in the affected file(s).

In /etc/apache2/apache2.conf, I tried:
ensuring 'KeepAlive' was 'On'
increasing 'MaxKeepAliveRequests' from '100' to '200'
and increasing 'KeepAliveTimeout' from '50'? to '300'

I'm not sure how scientific this was but it did seem to reduce the occurrences (but not to zero).

I've got no idea where to go from here in terms of whether this is a (Karmic) bug or just my (lack of) php skills.

---

### Post by fifth on 2009-08-23
Seems to be an often recurring problem, loads of google search results on this problem for the last few years across all distros.

Confirmed its not my code anyway :D Just had the same problem with phpMyAdmin, firefox was showing the download dialog for the php file.

[edit]

Just remembered I am also occassionaly getting the following from suhosin;

```

[Sun Aug 23 22:51:54 2009] [error] [client 127.0.0.1] ALERT-SIMULATION - canary mismatch on efree() - heap overflow detected (attacker '127.0.0.1', file '/home/user/dev/include/session.php', line 33

```

Although I've got suhosin in simulation mode to see if the problem went away, it made no difference. btw, line 33 is "session_start();"

---

### Post by mphill on 2009-09-04
I'm having this issue, I'm convinced it's a PHP issue and not Apache.  Lighttpd+php5-cgi exhibits the same random failure, at about a 3/4 rate.  Memory settings don't affect anything so don't waste your time.

---

### Post by BackwardsDown on 2009-09-05
I'm having the same issue, anyone that has a solution?

---

### Post by fifth on 2009-09-05
Glad its been confirmed but sorry haven't found a work-around yet. However bug report has now been filed;

[Bug #424789]("https://bugs.launchpad.net/ubuntu/+source/php5/+bug/424789")

If this affecting you please add to the affected list.

---

### Post by fifth on 2009-09-06
May have a temporary work-around for this problem. Early testing seems to be working well.

Edit the files

```

/etc/php5/apache2/conf.d/suhosin.ini
/etc/php5/conf.d/suhosin.ini

```

uncomment and change the line

```
suhosin.session.encrypt = off
```

Then restart apache for the change to take effect;

```
sudo /etc/init.d/apache2 restart
```

The bug is discussed in gentoo [here]("http://bugs.gentoo.org/show_bug.cgi?id=276583")

---

### Post by BackwardsDown on 2009-09-06
> **fifth said:**
> May have a temporary work-around for this problem. Early testing seems to be working well.
If it works, totally super and thanks! :D

---

### Post by fifth on 2009-09-06
> **BackwardsDown said:**
> If it works, totally super and thanks! :D

Definitely working for me :D

[edit]

This issue is also being discussed [here]("http://www.dotdeb.org/2009/06/25/php-5-2-10-packages-for-lennyetch-are-now-available/") where the recommendation is to downgrade to 5.2.9.

---

### Post by joekki on 2009-09-06
Finally a workaround for this. Now my 10 virtual hosts are up and working again, thanks to Fifth! Simulation didn't worked out for me either.

---

### Post by fifth on 2009-09-06
Glad it helped. Seems 5.2.11 is one its way to resolve the problem, although I'm not sure of the ubuntu package situation ... would assume the new packages will find there way here when available.

[edit]

Although the 5.3 are close by too ...

---

### Post by fifth on 2009-09-06
> **joekki said:**
> Finally a workaround for this. Now my 10 virtual hosts are up and working again, thanks to Fifth! Simulation didn't worked out for me either.

I needed a workaround for this, debugging php forms was beginning to be a real pain lol.

---

### Post by fifth on 2009-09-11
For anyone still getting segfaults after the changes I suggested, try also changing the file;

```
/etc/php5/conf.d/suhosin.ini
```

and making the same changes, ie

```
suhosin.session.encrypt = off
```

I think we have two versions of Suhosin. One package installed by default with a LAMP setup (php5-suhosin) and also patched into the current version of PHP5.

Can anyone confirm?

---


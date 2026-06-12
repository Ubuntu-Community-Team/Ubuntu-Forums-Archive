---
title: "Kompozer problem with Intrepid"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Gina on 2008-10-10
As I'm now using Intrepid for almost everything, I decided to get my website editing and publishing working in Intrepid too (been using Hardy).  Using Kompozer for page editing and FileZilla for FTP.  Most things seem to work except creating links in Kompozer.  When trying to set a link for marked text it shuts down - completely disappearing from the screen.

I've done a search for this bug but found nothing so I'm wondering is anyone else is using Kompozer and found this bug.

---

### Post by plun on 2008-10-11
I just tested this and it works for me.

Testcase as HTML

```
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
<html>
<head>
  <meta content="text/html; charset=ISO-8859-1"
 http-equiv="content-type">
  <title></title>
</head>
<body>
<a href="http://www.kompozer.net/">Kompozer</a><br>
<br>
<a href="http://www.kompozer.net/" target="_blank">Test</a>
</body>
</html>

```

First using menu > Insert > Link  and then using the toolbar

Run kompozer from terminal and look for errors

Using ver 0.7.10 from Intrepids repo

---

### Post by Sand &amp; Mercury on 2008-10-11
I'm having the same problem. It also dies when I'm inserting images. Worked perfectly fine in Hardy.

---

### Post by plun on 2008-10-11
Yup images kills Kompozer also for me...

```
plun@plun:~$ kompozer
pure virtual method called
terminate called without an active exception
Aborted (core dumped)

```

---

### Post by ZarathustraDK on 2008-10-13
Got the same problem. Kompozer crashes to desktop when changing background-color on a page.

Upgraded from Hardy to Intrepid, not a fresh install.

---

### Post by pluckypigeon on 2008-10-20
same problem:)

---


---
title: "Cannot open local files in Firefox 9.01"
date: 2012-01-28
forum: Installation &amp; Upgrades
---

### Post by 4partee on 2012-01-28
My local html file links no longer work inFirefox.  

My desktop IS my server!!!!!!!!!!!!

Here is an example that does not work as of today's update to Firefox 9.0.1!!!

	echo "<td align='left' <a target='_blank' href=\"/aam/foliofn/u_oc_list_symbol.php?s=$symbol\" >$symbol</a> </td>";


This is from a php dynamic html program that worked this morning!!!


I NEED this to work by Monday AM.

---

### Post by CharlesA on 2012-01-28
Ok. What sort of php code are you running? I just checked my site with Firefox 9 and it showed up fine and I have a few php "print" and "echo" statements

Are you getting any error messages?

---

### Post by 4partee on 2012-01-28
I have attached two screenshots:

'debian' is running in Virtualbox.  The columns Symbol and sma20 show working links in Blue.  If I click on the value 6.7 another local php program runs and shows info from a child tabe.

'U10.4' does not show in Blue and the values are not clickable. 

 Before running 'Update Manager' the links were ok.

---

### Post by CharlesA on 2012-01-29
Check the page source to see what it is rendering it as.

---

### Post by 4partee on 2012-01-29
P.S.

Chromium 15.0.874.106 (Developer Build 107270 Linux) Ubuntu 10.04 is also failing to show the Blue links!

Apparmor problem?

---

### Post by CharlesA on 2012-01-29
I doubt it. Check the page source and validate your code. I use TotalValidator for that.

---

### Post by 4partee on 2012-01-29
> **CharlesA said:**
> Check the page source to see what it is rendering it as.

<td align='right' <a target='_blank' href="list_fvall_symbol.php?s=VIVO&m=2012-01-27&i=interval 1 month " >-6.7</a> </td>

---

### Post by CharlesA on 2012-01-29
Forgot to close the td tag, it should look something like this:

<td align='right'><a target='_blank' href="list_fvall_symbol.php?s=VIVO&m=2012-01-27&i=interval 1 month ">-6.7</a></td>

---

### Post by 4partee on 2012-01-29
> **CharlesA said:**
> I doubt it. Check the page source and validate your code. I use TotalValidator for that.

Installing TotalValidator.

---

### Post by CharlesA on 2012-01-29
Depending on what version of html you are using, it probably should look more like this:

```
<td align="right"><a target="_blank" href="list_fvall_symbol.php?s=VIVO&m=2012-01-27&i=interval 1 month ">-6.7</a></td>
```

---

### Post by 4partee on 2012-01-29
> **CharlesA said:**
> Depending on what version of html you are using, it probably should look more like this:

```
<td align="right"><a target="_blank" href="list_fvall_symbol.php?s=VIVO&m=2012-01-27&i=interval 1 month ">-6.7</a></td>
```

Whew! Thanks, I have it now.

I have a lot of fixing to do now.

Here is what worked:
<td align='right' ><a target='_blank' href="list_fvall_symbol.php?s=VIVO&m=2012-01-27&i=interval 1 month " >-6.7</a> </td>

Pesky little >

---

### Post by CharlesA on 2012-01-29
Indeed. Just out of curiosity, what version of HTML are you using? My site is using XHTML-strict.

TotalValidator helps quite a bit with catching small coding errors.

---

### Post by 4partee on 2012-01-29
> **CharlesA said:**
> Indeed. Just out of curiosity, what version of HTML are you using? My site is using XHTML-strict.

TotalValidator helps quite a bit with catching small coding errors.

Don't really know what version. Never thought of it that way!  99% of the time I am using html with PHP to list mysql table contents through the browser.  I don't run a site for public use.  I use bluefish editor.

When I try to use Total Validator I get:
Basic tool not found. Download and install it, or check the 'Path to tool'.

---

### Post by CharlesA on 2012-01-29
> **4partee said:**
> Don't really know what version. Never thought of it that way!  99% of the time I am using html with PHP to list mysql table contents through the browser.  I don't run a site for public use.  I use bluefish editor.

When I try to use Total Validator I get:
Basic tool not found. Download and install it, or check the 'Path to tool'.
You have a [doctype declaration]("http://www.w3schools.com/tags/tag_doctype.asp"), right?

Huh, you should just be able to unpack the tar somewhere and run it by double-clicking on total_validator.sh

Make sure you have java installed as it is a java application.

---

### Post by 4partee on 2012-01-29
> **CharlesA said:**
> You have a [doctype declaration]("http://www.w3schools.com/tags/tag_doctype.asp"), right?

Huh, you should just be able to unpack the tar somewhere and run it by double-clicking on total_validator.sh

Make sure you have java installed as it is a java application.

Nope! Don't use doctype. I waste no time getting into PHP.  Almost exclusive use of PHP/mysql table driven dynamic output.

I added doctype to the program like this:
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
       "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
       
<?php

echo "<title>List VIG</title>";

include('connect.php');
$now   = date('Y-m-d H:i:s');
list($maxfiledate) = mysql_fetch_row(mysql_query("select max(filedate) from fvall"));
echo " <HR><B>It is now $now, AS-OF $maxfiledate</B></HR>";

....
and I see no change. All seems to be working again. 

What tar? I installed as an add-on under FF tools.

Yes, have java. Whatever is standard in U10.4.

---

### Post by CharlesA on 2012-01-29
There won't be any change, the doctype just tells the browser what version/standard of html you are using.

Ah the addon, I use the [standalone version]("http://www.totalvalidator.com/downloads/totalvalidatorbasic.tar.gz") so I am not sure why you are getting that message.

---


---
title: "Installing XAMPP on linux problem"
date: 2006-10-24
forum: Installation &amp; Upgrades
---

### Post by Dark_Dragon on 2006-10-24
Well thanks to the help of another member on here i found XAMPP but  even following the instructions on the accompanying site (sry for spelling :S) it wont run. i have unzipped it as root to /opt/LAMPP as it said and tryed to run it but it sint a valid command (/opt/lampp start) 

any ideas on how to fix/install it properly?

thanks

-- DD

* im using Dapper if thats a help

---

### Post by az on 2006-10-24
> **Dark_Dragon said:**
> Well thanks to the help of another member on here i found XAMPP but  even following the instructions on the accompanying site (sry for spelling :S) it wont run. i have unzipped it as root to /opt/LAMPP as it said and tryed to run it but it sint a valid command (/opt/lampp start) 

any ideas on how to fix/install it properly?

thanks

-- DD

* im using Dapper if thats a help
Unix is case sensitive.

Try /opt/LAMPP instead of /opt/lampp

---

### Post by Dark_Dragon on 2006-10-25
rofl I dunno y i never thought of that lol thanks ill try that :)

---

### Post by oldbeggar on 2006-10-25
You have to uzip it use this command:
tar -vxzf lampp.tar.gz /opt/lampp

---

### Post by Dark_Dragon on 2006-10-25
i got it working lol that command line on the site is wrong... it tells u to run the dir rather than the script lol, so it was /opt/lampp/lampp start :) its working now thanks all :)

---


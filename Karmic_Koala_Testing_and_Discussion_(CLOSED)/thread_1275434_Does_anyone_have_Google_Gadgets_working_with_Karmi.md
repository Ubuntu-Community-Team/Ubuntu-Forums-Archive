---
title: "Does anyone have Google Gadgets working with Karmic?"
date: 2009-09-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by crjackson on 2009-09-25
Is anyone else seeing this error?  How can I fix this?

---

### Post by oboedad55 on 2009-09-26
> **crjackson said:**
> Is anyone else seeing this error?  How can I fix this?

I'm having the same problem...

---

### Post by dinxter on 2009-09-26
yep, does someone want to 
$ubuntu-bug google-gadgets-gtk
this?

---

### Post by dinxter on 2009-09-26
also effects google-gadgets-qt

---

### Post by dinxter on 2009-09-26
[https://bugs.launchpad.net/ubuntu/+source/google-gadgets/+bug/434127](https://bugs.launchpad.net/ubuntu/+source/google-gadgets/+bug/434127)

---

### Post by crjackson on 2009-09-27
Thanks, I'm glad I'm not the only one.

---

### Post by crjackson on 2009-10-11
Works fine with latest updates. :)

---

### Post by dinxter on 2009-10-11
> **crjackson said:**
> Works fine with latest updates. :)

what version are you using, i still get this on 0.10.5-0.2ubuntu1

---

### Post by crjackson on 2009-10-11
I got it from the repositories.

---

### Post by dinxter on 2009-10-11
hmm, i still get the bug unless i run
$ggl-qt -s qt
all other incarnations are broken for me

---

### Post by P4man on 2009-10-11
still doesnt work for me (and Im up to date). Launching ggl-gtk from the command line, I get:

```
Not a regular file: /
Failed to find proper Gecko Runtime Environment!

```

---

### Post by crjackson on 2009-10-11
I'm using the gtk version.

---

### Post by dinxter on 2009-10-11
is this with xulrunner 1.9.1 installed?

---

### Post by crjackson on 2009-10-11
> **dinxter said:**
> is this with xulrunner 1.9.1 installed?

yes

---

### Post by crjackson on 2009-10-18
> **crjackson said:**
> Is anyone else seeing this error?  How can I fix this?

Well after a clean install, it's back.  And no updates seem to be helping this time.

---

### Post by williejones on 2009-10-19
My google gadgets are not working also.

$ ggl-gtk
```
Not a regular file: /
Not a regular file: /
Not a regular file: /
No permission to read file.
No permission to access device status.
No permission to access device status.
No permissions to access D-Bus.
The program 'ggl-gtk' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAtom (invalid Atom parameter)'.
  (Details: serial 292 error_code 5 request_code 19 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
ggl-gtk: symbol lookup error: /usr/lib/libcurl-gnutls.so.4: undefined symbol: curl_mvaprintf, version CURL_GNUTLS_3

```

---

### Post by williejones on 2009-10-19
My google gadgets are not working also.

$ ggl-gtk
Not a regular file: /
Not a regular file: /
Not a regular file: /
No permission to read file.
No permission to access device status.
No permission to access device status.
No permissions to access D-Bus.
The program 'ggl-gtk' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAtom (invalid Atom parameter)'.
  (Details: serial 292 error_code 5 request_code 19 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
ggl-gtk: symbol lookup error: /usr/lib/libcurl-gnutls.so.4: undefined symbol: curl_mvaprintf, version CURL_GNUTLS_3


Edit how do you delete post?

---

### Post by dinxter on 2009-10-20
js-script bug with xulrunner-1.9.1 and BadAtom on ggl-gtk should hopefully be cured in 0.10.5-0.2ubuntu2
seems to at least work in gtk/qt versions now

---

### Post by crjackson on 2009-10-20
> **dinxter said:**
> js-script bug with xulrunner-1.9.1 and BadAtom on ggl-gtk should hopefully be cured in 0.10.5-0.2ubuntu2
seems to at least work in gtk/qt versions now

How is the world was it possible that it was working previously?  Any clue?

---

### Post by dinxter on 2009-10-20
> **crjackson said:**
> How is the world was it possible that it was working previously?  Any clue?
No clue at all, that did confuse me a bit. xulrunner-1.9.1 support hadnt been added yet so it shouldn't have been possible that it worked, who knows. I'm used to being confused though :)

---

### Post by crjackson on 2009-10-20
> **dinxter said:**
> No clue at all, that did confuse me a bit. xulrunner-1.9.1 support hadnt been added yet so it shouldn't have been possible that it worked, who knows. I'm used to being confused though :)

Point is moot now anyway.  Latest batch of updates fixed for me again.

---

### Post by lovinglinux on 2009-10-20
> **crjackson said:**
> Point is moot now anyway.  Latest batch of updates fixed for me again.

Confirmed. Also working here.

---

### Post by williejones on 2009-10-20
Today's update got it working for me.

---


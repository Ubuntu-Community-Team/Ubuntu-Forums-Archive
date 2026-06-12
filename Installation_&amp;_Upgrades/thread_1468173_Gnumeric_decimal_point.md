---
title: "Gnumeric decimal point"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by Logi505 on 2010-05-01
Hi,

can someone please tell how can I configure Gnumeric that I will have instead of dots a decimal points. I have all ready tried to install Gnumeric in windows and everything works OK. I was also looking threw settings in Gnumeric under windows environment and try to put the same settings under ubuntu 10.4 with no luck. 

Thanks for help.

---

### Post by jbrefort on 2010-05-01
What difference do you see between a dot and a decimal point. Both are unicode character 0x2E.

In gnumeric, the decimal separator is locale dependent. Might be a dot or a comma, generally (there might be other characters used in locales I don't know).
The appropriate decimal separator is entered when you use the numpad, at least on linux. There is a gtk bug in win32 which make things not work. Also some keyboard layouts are known to be buggy (they return dot instead of decimal separator).
I hope this help.

---

### Post by Logi505 on 2010-05-02
Thanks fro your reply. 

I'm not sure if I understand correctly. But the whole problem is if I enter in the column 0,9876 and press enter I get 9876 
Now, if I enter a 0.9876 i get 0.9876 just the way I wanted only with " , "
I would like to use gnumeric with , instead of .
Is there a way to do just that.

Thank you for your help.

---

### Post by jbrefort on 2010-05-02
This is a locale issue. If your locale use the comma as decimal separator, it should work as you wish. What's your locale?

---

### Post by Logi505 on 2010-05-02
Thanks for reply.

I know and that is the problem. In calc it uses my locale settings which is EU - Slovenia, which it shows with comma. But in gnumeric I can't configure it to show me a comma.

---

### Post by jbrefort on 2010-05-02
Try (from the command line):
LC_NUMERIC="sl" gnumeric

If it does not work, do you see any error message?

---

### Post by Logi505 on 2010-05-02
(gnumeric:5658): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

This is what I get.

---

### Post by jbrefort on 2010-05-02
Ok, this explains what happens. The locale has not been generated on installation (this is quite weird, btw).

Edit /etc/locale.gen, and remove the '# ' chars of the appropriate line which should be:
# sl_SI.UTF-8 UTF-8
so that it becomes:
sl_SI.UTF-8 UTF-8

(you can do that using sudo gedit /etc/locale.gen).

Then run:
sudo locale-gen

Things should work much better.

---

### Post by Logi505 on 2010-05-02
Thank you jbrefort it all works fine now. There was no language support installed on my system. So I installed the language, set language as a English and text as Slo and Gnumeric started to show comma.

But if open /etc/locale.gen there is nothing in it. Is this normal ? 


Thanks again for your help

---

### Post by jbrefort on 2010-05-02
I suppose it's normal. Anyway, if things work, don't care ;-).
Btw, I'm using Debian, not Ubuntu, so things might be a bit different.

---

### Post by Logi505 on 2010-05-02
OK, Thanks again for all your help and support.

---


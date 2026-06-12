---
title: "Xorg Character Encoding"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by bookmark_jn on 2007-03-03
Ubuntu can't open files of my native language, (Turkish [ISO-8859-9]) 


Must this: (ISO-8859-9)
[IMG]http://img404.imageshack.us/img404/7605/26811446kw5.gif[/IMG]

But gives me this (ISO-8859-1)

[IMG]http://img469.imageshack.us/img469/2331/63383923iy7.png[/IMG]

I used all text editors all of them same. I think I must set a default xorg encoding. 

Locales:

```
        LANGUAGE = "tr_TR:tr:en_GB:en",
        LC_ALL = "ISO-8859-9",
        LANG = "tr_TR"

```

Note: I can write my native language(Turkish). Then I can open file with true encoding (Turkish encoding). But if I download a file from internet or use my windows XP texts gives me wrong encoding.

How can I set this setting?

---

### Post by Boy_Ubunntuu on 2007-03-03
Edit ```
sudo gedit /etc/environment
```
add this
```
LANGUAGE="tr_TR:tr"
```

Worked?

---

### Post by bookmark_jn on 2007-03-03
No, didn't work :(

---

### Post by Boy_Ubunntuu on 2007-03-05
I dont know, maybe someone alse can help. Or IT CAN BU A BUG OF UBUNTU!

---

### Post by bookmark_jn on 2007-03-06
[Linux programlar&#305;]("http://www.yeniklasor.com/list.php?c=linux-program")

Maybe can be a bug yes.

---

### Post by Narf on 2007-05-08
I have the same problems with cyrilic encodings.
As far as I can tell, it looks like Feisty only supports UTF-8 charset, and that kinda makes me sad.

---


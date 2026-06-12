---
title: "Locale en_CH not supported: get often the error &quot;locale not supported by c library&quot;"
date: 2005-08-11
forum: Installation &amp; Upgrades
---

### Post by phibuntu on 2005-08-11
New to ubuntu

I live in switzerland and my system is installed in english, so I want to use the locale "en_CH".
Very often I get the message "locale not supported by c library".

Where can I specify the country, where the language? 
Is it easy to generate a new locale in 
/usr/share/i18n/locales ???
(I have seen, that en_CH is not mentioned in this directory.)

What is the prefered way to support my locale? Which files and environment variables do I have to change?

---

### Post by phibuntu on 2005-08-12
I tried a bit myself, but still have this error.

output of ">locale" is:
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_CH.ISO-8859-1
LC_CTYPE="en_CH.ISO-8859-1"
LC_NUMERIC="en_CH.ISO-8859-1"
LC_TIME="en_CH.ISO-8859-1"
LC_COLLATE="en_CH.ISO-8859-1"
LC_MONETARY="en_CH.ISO-8859-1"
LC_MESSAGES="en_CH.ISO-8859-1"
LC_PAPER="en_CH.ISO-8859-1"
LC_NAME="en_CH.ISO-8859-1"
LC_ADDRESS="en_CH.ISO-8859-1"
LC_TELEPHONE="en_CH.ISO-8859-1"
LC_MEASUREMENT="en_CH.ISO-8859-1"
LC_IDENTIFICATION="en_CH.ISO-8859-1"
LC_ALL=

---------------

Starting most application I get the following error (here I start synaptic):
(synaptic:8468): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

-----------
/etc/environment looks like this:
LANGUAGE="en_CH:en"
LANG=en_CH.ISO-8859-1

JAVA_HOME=/usr/java

------------
I added a new locale in /usr/share/i18n/locales/ called "en_CH" which is a mix of en_GB and de_CH having all language specific thigns like in GB, but the rest (currency, ...) like CH.
----------------

Any idea?

Is there a "howto locale and languages"?

---

### Post by rwabel on 2005-08-15
never heard of en_CH! I don't think that it exists, but teach me otherwise.

Why not use en_US.UTF-8 for the OS language and for LC_XXX you want to have in your local, choose the swiss version. I think it's de_CH

---

### Post by phibuntu on 2005-08-16
thanks for your prompt answer.

en_CH does not exist (I dont't think the english minority in switzerland exists  :???: ). Thats why I created the file en_CH in /usr/share/i18n/locales/. 
I read and write in english, but I live in switzerland. 

My problem is, that I do not understand how ubuntu reads and treats the "LANG, LANGUAGE, LOCALE, LC_*, ..." files.
:?:

any Idea, which documents describes this?

The solution should provide the following:

- OS language: english
- user languages: english / german (each user defines himself)
- currency, metrics, date-formats: swiss-german (for all users)
- the error "locale not supported by c library" should no longer appear and lead to strange results like date-formats not understood by users (like 3/4/05).

Any help is welcome.

---

### Post by rwabel on 2005-08-16
[QUOTE=phibuntu]thanks for your prompt answer.

en_CH does not exist (I dont't think the english minority in switzerland exists  :???: ). Thats why I created the file en_CH in /usr/share/i18n/locales/. 
I read and write in english, but I live in switzerland. 

My problem is, that I do not understand how ubuntu reads and treats the "LANG, LANGUAGE, LOCALE, LC_*, ..." files.
:?:

any Idea, which documents describes this?

The solution should provide the following:

- OS language: english
- user languages: english / german (each user defines himself)
- currency, metrics, date-formats: swiss-german (for all users)
- the error "locale not supported by c library" should no longer appear and lead to strange results like date-formats not understood by users (like 3/4/05).

Any help is welcome.[/QUOTE]
 I see your point. OS language and user languages is often the same. That' how I understand it:
Each user can change it's language (that you can decide at the login in GDM or KDM).
You can easily change your metrics and stuff to de_CH.UTF-8.
I don't know what all the different types mean, but you can surely find them via google.

About the error message, mhh I have no idea how to define them. 

As a little hint, try also to search in the french and german forums, they have for sure more information about localization stuff. Let me know how it's going

---

### Post by phibuntu on 2005-09-04
I have not found the ultimate solution, but I live with the following workaround.

sudo dpkg-reconfigure localedef
> language en_GB
> all other locale-settings: ch_DE

The error messages are now gone away and most programs I use don't care about locales anyway ;-)

---

### Post by rduke15 on 2006-05-12
I found this blog entry with detailed easy steps to create an en_CH locale in Sarge. It probably works in Ubuntu as well.

[http://alma.ch/blogs/bahut/2006/04/ench-locale.html]("http://alma.ch/blogs/bahut/2006/04/ench-locale.html")

---


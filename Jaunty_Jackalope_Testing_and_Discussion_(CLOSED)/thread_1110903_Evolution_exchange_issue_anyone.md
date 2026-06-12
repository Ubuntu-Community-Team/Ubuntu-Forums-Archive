---
title: "Evolution exchange issue anyone?"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jackocleebrown on 2009-03-30
Does anyone else see problems with evolution using the exchange back-end in Jackalope beta?

I get a crash as soon as evolution tries to authenticate to an exchange server and this output on the command line:

```
** (evolution:8926): WARNING **: Unexpected kerberos error -1765328164
** (evolution:8926): DEBUG: mailto URL command: evolution %s
** (evolution:8926): DEBUG: mailto URL program: evolution
** (evolution:8926): DEBUG: EI: SHELL STARTUP

GThread-ERROR **: file /build/buildd/glib2.0-2.20.0/gthread/gthread-posix.c: line 171 (g_mutex_free_posix_impl): error 'Device or resource busy' during 'pthread_mutex_destroy ((pthread_mutex_t *) mutex)'
aborting...
Aborted (core dumped)
```

I have not seen anyone else mention this problem but I am sure that others must see it... or am I the only one who uses exchange with evolution??

Thanks, Jack.

---

### Post by xtoudi on 2009-03-30
> **jackocleebrown said:**
> Does anyone else see problems with evolution using the exchange back-end in Jackalope beta?

I get a crash as soon as evolution tries to authenticate to an exchange server and this output on the command line:

```
** (evolution:8926): WARNING **: Unexpected kerberos error -1765328164
** (evolution:8926): DEBUG: mailto URL command: evolution %s
** (evolution:8926): DEBUG: mailto URL program: evolution
** (evolution:8926): DEBUG: EI: SHELL STARTUP

GThread-ERROR **: file /build/buildd/glib2.0-2.20.0/gthread/gthread-posix.c: line 171 (g_mutex_free_posix_impl): error 'Device or resource busy' during 'pthread_mutex_destroy ((pthread_mutex_t *) mutex)'
aborting...
Aborted (core dumped)
```

I have not seen anyone else mention this problem but I am sure that others must see it... or am I the only one who uses exchange with evolution??

Thanks, Jack.

Looks like you are conecting to Exchange using OWA - it's old and working method. The new one is using Mapi Exchange (required evolution-mapi package) - but so far it is not working. There is thread about Evo here and some other ones on ubuntuforums - have to search for it.

Almost forgot ... my Evolution works well with Exchange 2003/2007 OWA.

---

### Post by jackocleebrown on 2009-03-30
Yes, I am using the OWA method of access. I have just tried out the new evolution-mapi package and I can get that to work ok..... will just be a pain to migrate other settings etc.

Thanks for your help. Jack.

---

### Post by pveith on 2009-03-30
Huh? You can actually get messages through evolution-mapi? In my install i just get the folders, but no content. As this behaviour seems to be "normal" reading through launchpad and evolution mailinglist, i did not inquire further. So just out of curiousity: Is there a known way to actually receive email-messages using the new mapi-evo-plugin in jaunty?

---

### Post by xtoudi on 2009-03-30
> **pveith said:**
> Huh? You can actually get messages through evolution-mapi? In my install i just get the folders, but no content. As this behaviour seems to be "normal" reading through launchpad and evolution mailinglist, i did not inquire further. So just out of curiousity: Is there a known way to actually receive email-messages using the new mapi-evo-plugin in jaunty?

I wrote this:

[COLOR="SeaGreen"]info from MAPI FAQ:

[I][B]..." I've specified all the details correctly, but I'm unable to get past the Authentication?

Please make sure:

    * Your mailbox is enabled for MAPI (This is a setting on the server).
    * Your Exchange server has Public Folders set up (There have been some issues observed if there is no PF hierarchy setup on the server). "...[/B][/I]

[http://www.go-evolution.org/MAPI_FAQ#Compiling_from_source](http://www.go-evolution.org/MAPI_FAQ#Compiling_from_source)

And if you want to play with compiling:
[http://www.go-evolution.org/MAPIProvider](http://www.go-evolution.org/MAPIProvider)[/COLOR]

**...here:**
[http://ubuntuforums.org/showthread.php?t=1090381&page=3](http://ubuntuforums.org/showthread.php?t=1090381&page=3) - thread: **Evolution-mapi working or not?**

But if you have forlders it means at least you are in front!! Most of us cannot even authenticate using exch-mapi!

---

### Post by pveith on 2009-03-30
Uh, just started my jaunty-computer and it simply works. 2 weeks ago i just coundn't get it to work at all and now it simply works (just some minor character-encoding probs). I started to compile evo myself, but just did not find the time to actually do so. 


Thanks for the links and quick reply. Obviously the evolution-mapi team and the packagemanager of ubuntu are doing a great job!

---

### Post by jackocleebrown on 2009-03-30
It just worked for me. I installed the evolution-mapi package, cleared the .evolution folder and answered the questions in the setup assistant.

---

### Post by xtoudi on 2009-03-30
> **jackocleebrown said:**
> It just worked for me. I installed the evolution-mapi package, cleared the .evolution folder and answered the questions in the setup assistant.

So you are lucky guy!! This plugin has still to many bugs and in most cases it doesn't work. I've just cleared .evolution as you said and it doesn't work. 

Authentication error.
CreateProfileStore:Mapi_E_NO_ACCES

---

### Post by jackocleebrown on 2009-03-30
I spoke too soon, sending mail does not seem to work.
And annoyingly I can't seem to get a simple STMP account to send mail either!

---

### Post by xtoudi on 2009-03-30
Finnaly, so far:
Evolution Exchange "traditional" package (OWA) is the only way to connect to Exchange - and it really works (in my case: Jaunty BETA, gnome 2.26 - all up2date).

---

### Post by jackocleebrown on 2009-03-30
It seems like this is a more general send mail bug, I cannot send mail to anyone in one of my address books. It looks like evolution is stripping the addresses. If I look in my outbox after I click send I can see the message but it has lost its recipients. If I send to an address not in an address book it works fine.

---

### Post by newtech13 on 2009-04-07
I have also big problem with evolution and probably evolution-exchange in fact. Since upgrade to jaunty Beta2 I have a crash with :

GThread-ERROR **: file /build/buildd/glib2.0-2.20.0/gthread/gthread-posix.c: line 171 (g_mutex_free_posix_impl): error 'Périphérique ou ressource occupé' during 'pthread_mutex_destroy ((pthread_mutex_t *) mutex)'

OWA is the unique access authorized for my enterprise mail so it is very annoying. In fact thinking of downgrade to 8.10

---

### Post by newtech13 on 2009-04-07
I've got evolution to start with "evolution --disable-eplugin".
But exchange seems to not work.

---

### Post by wladyx on 2009-04-10
I get this too on arch.
Did anyone found an upstream bug report that we can track?
Thanks.

---

### Post by moore.bryan on 2009-04-14
i've been able to get and send messages using evolution-mapi, but it won't send my deleted messages to the "deleted items" folder. any ideas?

---


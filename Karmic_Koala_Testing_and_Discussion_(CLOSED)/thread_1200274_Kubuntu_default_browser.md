---
title: "Kubuntu default browser"
date: 2009-06-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by descendent87 on 2009-06-29
Apparently Kubuntu devs are thinking about making Arora the default browser for Karmic, does anyone else think they should consider Rekonq instead? It fits in much better with KDE in my opinion

---

### Post by Blood//Stain//Child on 2009-06-29
As long as they kill Konqueror, I don't care.

---

### Post by frustphil on 2009-06-29
> **Blood//Stain//Child said:**
> As long as they kill Konqueror, I don't care.

+1

Rekonq looks more integrated in KDE...so I would choose it over Arora.

---

### Post by descendent87 on 2009-06-30
> **Blood//Stain//Child said:**
> As long as they kill Konqueror, I don't care.

Whats the problem with konqueror? I quite like it, still needs a bit of love to be ready to replace firefox but it's getting there

---

### Post by jamest09 on 2009-06-30
I like Konqueror, and I've started developing a great hatred of Firefox lately!

---

### Post by davesmith on 2009-07-01
I installed konqueror again recently but it wont boot up. Could anyone tell me how to use the terminal to start konqueror? Or indeed to use the terminal to start any program up

Tnx

---

### Post by aamukahvi on 2009-07-01
> **davesmith said:**
> I installed konqueror again recently but it wont boot up. Could anyone tell me how to use the terminal to start konqueror? Or indeed to use the terminal to start any program up

Tnx
type "konqueror" and hit enter

---

### Post by davesmith on 2009-07-01
Thanks, I tried that - but I got a series of errors, here is the terminal output:

<  konqueror
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/toshiba/.DCOPserver_laptop__0
and start dcopserver again.
---------------------------------

KDE Daemon (kded) already running.
kbuildsycoca running...
kbuildsycoca: WARNING: KTempFile: Error trying to create /var/tmp/kdecache-toshiba/ksycocaXXXXXX.new: Permission denied
kbuildsycoca: ERROR creating database '/var/tmp/kdecache-toshiba/ksycoca'! No such file or directory
kio (KMimeType): WARNING: KServiceType::offers : servicetype Browser/View not found
trying to create local folder /var/tmp/kdecache-toshiba/favicons: Permission denied
kio (KMimeType): WARNING: KServiceType::offers : servicetype KonqAboutPage not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype KonqAboutPage not found
konqueror: WARNING: KonqFactory::createView : no factory
konqueror: WARNING: Profile Loading Error: View creation failed


And that is after installing!

Is there an easy fix for this issue? It looks to me like it might be a permissions thing

Tnx

---

### Post by garba on 2009-07-01
i'm all for khtml's demise once and for all

---

### Post by frustphil on 2009-07-01
> **davesmith said:**
> Thanks, I tried that - but I got a series of errors, here is the terminal output:

<  konqueror
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/toshiba/.DCOPserver_laptop__0
and start dcopserver again.
---------------------------------

KDE Daemon (kded) already running.
kbuildsycoca running...
kbuildsycoca: WARNING: KTempFile: Error trying to create /var/tmp/kdecache-toshiba/ksycocaXXXXXX.new: Permission denied
kbuildsycoca: ERROR creating database '/var/tmp/kdecache-toshiba/ksycoca'! No such file or directory
kio (KMimeType): WARNING: KServiceType::offers : servicetype Browser/View not found
trying to create local folder /var/tmp/kdecache-toshiba/favicons: Permission denied
kio (KMimeType): WARNING: KServiceType::offers : servicetype KonqAboutPage not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype KonqAboutPage not found
konqueror: WARNING: KonqFactory::createView : no factory
konqueror: WARNING: Profile Loading Error: View creation failed


And that is after installing!

Is there an easy fix for this issue? It looks to me like it might be a permissions thing

Tnx

type sudo apt-get remove konqueror...

---

### Post by davesmith on 2009-07-02
Thanks for the suggestions. I have tried sudo apt-get remove konqueror, and then re-installing it. It still wont work, maybe because it cant access a tmp file. Thats why I think its a permissions thing 

Does anyone know how to use the terminal to change the root permissions for this tmp file? Or any other way to get it to start?

I like konqueror as a file browser, its faster than anything else

---

### Post by taavikko on 2009-07-02
> **davesmith said:**
> Thanks for the suggestions. I have tried sudo apt-get remove konqueror, and then re-installing it. It still wont work, maybe because it cant access a tmp file. Thats why I think its a permissions thing 

Does anyone know how to use the terminal to change the root permissions for this tmp file? Or any other way to get it to start?

I like konqueror as a file browser, its faster than anything else

To fully purge konquerors settings use this
```
sudo aptitude purge konqueror && rm -r ~/.kde/share/{apps,config}/konqueror* && sudo aptitude install konqueror
```

Note: will erase all the existing bookmarks and such, so take a backup of them before.

---

### Post by taavikko on 2009-07-02
And on topic, Arora has quickly got my affection :)
Fast browser, but still missing few features (bookmarks import/export) (button for homepage)
(unable to use java-applets)

---

### Post by davesmith on 2009-07-02
Taavikko, thank you for your help. I will try the code, but how can I take a back-up of my konqueror bookmarks? It wont boot up...are they in the filesystem somewhere?

---

### Post by taavikko on 2009-07-02
> **davesmith said:**
> Taavikko, thank you for your help. I will try the code, but how can I take a back-up of my konqueror bookmarks? It wont boot up...are they in the filesystem somewhere?

It's saved in a "~/.kde/share/apps/konqueror/bookmarks.xml" file
just copy that to safety
```
cp ~/.kde/share/apps/konqueror/bookmarks.xml ~/
```
That copies it to root of home folder.

---

### Post by davesmith on 2009-07-02
Taavikko

I used the purge code and it did remove konqueror and re-installed it. But it still wont start! Here is the terminal output after typing konqueror and pressing enter:-

< konqueror
kio (KMimeType): WARNING: KServiceType::offers : servicetype Browser/View not found
trying to create local folder /var/tmp/kdecache-toshiba/favicons: Permission denied
konqueror: WARNING: Can't open /home/toshiba/.kde/share/apps/konqueror/bookmarks.xml
kio (KMimeType): WARNING: KServiceType::offers : servicetype KonqAboutPage not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype KonqAboutPage not found
konqueror: WARNING: KonqFactory::createView : no factory
konqueror: WARNING: Profile Loading Error: View creation failed
toshiba@laptop:~$ 

Well I dont know what to do next, what is causing this issue?

---

### Post by descendent87 on 2009-07-03
> **taavikko said:**
> And on topic, Arora has quickly got my affection :)
Fast browser, but still missing few features (bookmarks import/export) (button for homepage)
(unable to use java-applets)
Arora can import and export bookmarks, it's in "file" menu

---

### Post by taavikko on 2009-07-04
> **descendent87 said:**
> Arora can import and export bookmarks, it's in "file" menu

Thanks, didn't saw it.
But now for the editing of bookmarks.
(sort alphabetically)

Good thing is that backspace action is working on mouse again.

---

### Post by forcecore on 2009-07-04
+1 to death for Konqueror and khtml, it even reduces size of Kubuntu 9.10 .iso

---

### Post by Changturkey on 2009-07-04
Arora isn't even version 1.0 yet, so give it some time. I think development will pick up once it gets more users.

---

### Post by keiichidono on 2009-07-05
> **forcecore said:**
> +1 to death for Konqueror and khtml, it even reduces size of Kubuntu 9.10 .iso

I +1 you sir. khtml isn't up to date and compliant. Any other modern browser (such as Chromium) would be better.

---

### Post by Zorael on 2009-07-05
I find myself using Chromium more and more despite its lack of plugin support and extensions. Firefox is just too unresponsive compared to Arora and Chromium, but the extensions keep me from getting rid of it completely.

+1 for getting rid of Konqueror. Pool the effort into polishing webkit and one of Arora/Rekonq instead.

---

### Post by taavikko on 2009-07-07
When clicking external urls, (e.g in irssi) KDE launches still konqueror.
This doesn't happen when I set "open http urls in a following browser" to arora (default applications)

But there's image links that I would like to view directly on Gwenview
(open in a application based on the contents of the url)

Should try adding arora to alternatives so it would override konqueror

---

### Post by inportb on 2009-07-07
I just reinstalled; it appears that arora is indeed the new default.

---

### Post by forcecore on 2009-07-08
this is great and there are lot of monts to end of 9.10 so arora developer has lot of time to finish most critical features that is needed for casual browsing.

Kubuntu will be lighter now too if konqueror is dead finally.

---

### Post by descendent87 on 2009-07-08
> **forcecore said:**
> this is great and there are lot of monts to end of 9.10 so arora developer has lot of time to finish most critical features that is needed for casual browsing.

Kubuntu will be lighter now too if konqueror is dead finally.

Konqueror is not dead and I'd guess it will still be included in kubuntu

---

### Post by inportb on 2009-07-08
Konqueror is not just a browser, though. It's like a universal KPart wrapper.

---

### Post by taavikko on 2009-07-14
Does anybody else see this?

paste&drag ends up in
```
[263259.530655] <6>arora[16235]: segfault at 60 ip 00007f714b91ab57 sp 00007fff761390d0 error 4 in libQtWebKit.so.4.5.2[7f714b261000+f6f000]
```

---

### Post by xeros on 2009-07-30
Too bad Konqueror is becoming worse and worse every KDE 4.x release.
I vote for Arora as default - it's great browser - just look at version 0.8.0.

---

### Post by Asraniel on 2009-07-30
For me konqueror gets better with every 4.x release. With 4.3 even facebook seems to work the way i want.

---

### Post by inportb on 2009-07-30
Why not just embed WebKit in Konqueror? It's definitely possible.

---

### Post by Asraniel on 2009-07-30
Search on planetkde, there is a perhaps one month old blog entry that gives a reason why not. If i remember right it has something to do with konqueror beeing too tightly integreated with khtml. It would probably be possible to make the webkit kpart work as good as the khtml kpart, but from what i remember its not as easy as to just swap the kpart

---

### Post by papangul on 2009-07-30
Aurora is still not suitable for heavy duty use, it is good for testing/demo purposes, so surprised to see it as the default in kubuntu.

---

### Post by inportb on 2009-07-30
> **Asraniel said:**
> Search on planetkde, there is a perhaps one month old blog entry that gives a reason why not. If i remember right it has something to do with konqueror beeing too tightly integreated with khtml. It would probably be possible to make the webkit kpart work as good as the khtml kpart, but from what i remember its not as easy as to just swap the kpart

So what? That's like creating a new browser such as Arora, except Arora is severely lacking in features compared to Konqueror.

---

### Post by Asraniel on 2009-07-30
I was just answering your question ;-)

---


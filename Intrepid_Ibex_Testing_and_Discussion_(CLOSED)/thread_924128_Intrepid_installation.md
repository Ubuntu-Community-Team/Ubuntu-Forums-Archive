---
title: "Intrepid installation"
date: 2008-09-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by MadsRH on 2008-09-19
Hi
I've just installed the Alpha 6 and I have noticed a few things:
The first thing I would like to comment on is the message you receive after the installation is complete. There should be added a timeout to that message.
 
[ATTACH]85766[/ATTACH]

Second, I really don't understand why the installer can't "guess" where I'm living when I have selected the default language - It should be able to do that. So in this first screen I select the my language, witch is Danish:
[IMG]http://www.justlookdifferent.com/wp-includes/images/postpics/Ubuntu%20screens/just_look_different_ubuntu_step1of7.jpg[/IMG]

And then I have to scroll all the way down to the bottom to find Europe and then Denmark.
[IMG]http://www.justlookdifferent.com/wp-includes/images/postpics/Ubuntu%20screens/just_look_different_ubuntu_step2of7.jpg[/IMG]


Just my experience running (and installing) Intrepid so far
//MadsRH

---

### Post by BackwardsDown on 2008-09-19
You can also click on a city, but indeed it would be better if he would have guessed it.

---

### Post by forumache on 2008-09-19
Yes,

except Spanish, English, Russian where it is difficult to detect the country, for the rest of the countries it should be easy.

I select Romanian language, it should be the initial guess that I live in Romania. If I emigrated somewhere else, it would be my task to ignore the initial selection and choose a new country from the list.

Anyway, it's not like you do it everytime, just at the installation time.

Have a nice weekend!

---

### Post by MadsRH on 2008-09-19
So do you think someone should suggest this to the installation-team or perhaps report it as a bug?

---

### Post by forumache on 2008-09-19
First I would check if someone else reported it already.

It might have a chance to be added in 9.04, as the new blueprints are created.

---

### Post by MadsRH on 2008-09-19
> **forumache said:**
> First I would check if someone else reported it already.

It might have a chance to be added in 9.04, as the new blueprints are created.

Your right, but I couldn't find anything similar so I've submitted a bug

---

### Post by forumache on 2008-09-19
Well done! Could you put the link to the bug here? This way other people could jump to the bug and add their comments.

---

### Post by Nano Geek on 2008-09-19
One thing I don't like about the new installer is the iTunes like bar indicating how much space is used by each partition. It looks kinda tacky, plus it's an obvious rip-off of Apple's design.

---

### Post by UbuWu on 2008-09-19
> **forumache said:**
> Well done! Could you put the link to the bug here? This way other people could jump to the bug and add their comments.

It is here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/272244](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/272244)

---

### Post by olskar on 2008-09-19
> **asjdfwejqrfjcvm msz34rq33 said:**
> One thing I don't like about the new installer is the iTunes like bar indicating how much space is used by each partition. It looks kinda tacky, plus it's an obvious rip-off of Apple's design.

I agree, it does not fit in. At least not with the current theme. It is the same bar Banshee is using btw to show space left on ipods..

---

### Post by MadsRH on 2008-09-19
> **olskar said:**
> I agree, it _does not fit in. At least not with the current theme_. It is the same bar Banshee is using btw to show space left on ipods..

+1

They are out of style.

---

### Post by fballem on 2008-09-19
> **forumache said:**
> Yes,

except Spanish, English, Russian where it is difficult to detect the country, for the rest of the countries it should be easy.

I select Romanian language, it should be the initial guess that I live in Romania. If I emigrated somewhere else, it would be my task to ignore the initial selection and choose a new country from the list.

Anyway, it's not like you do it everytime, just at the installation time.

Have a nice weekend!

In addition to Spanish, English, and Russian, you would have to add French and Portuguese, which are spoken in multiple parts of the world. Those are the ones that I know about - which are European languages. I don't know enough about the Asian languages to know of those that are used in multiple locations. To be honest, I think that the effort required to 'guess' where the user is, based on their language choice, is probably not worth the development time. What would be useful is additional translations where there are variations in the language use.

For example, in English, there are U.S. English and U.K. English, which are quite different. These are the main variations, but nearly every Commonwealth country has a variation. For example, in Canada, U.S. spelling is more frequently used, although we have retained 'col_our_' instead of 'col_or_'. It would be nice if there was a Canadian English variation. I know also that the French spoken in Québec has significant differences to the French spoken in France. I imagine that there are significant variations among the other 'common' languages as well.

If there are instructions on how to build a language package that's based on an existing language package, then there are some of us who could start to contribute something useful, for those of us whose programming skills are not up to snuff.

---

### Post by UbuWu on 2008-09-19
There are 31 languages which are an official language in more than one country. See: [http://en.wikipedia.org/wiki/List_of_official_languages](http://en.wikipedia.org/wiki/List_of_official_languages)

That still leaves 84 languages for which the country could automatically be guessed.

---

### Post by cjwatson on 2008-09-19
The installer was always supposed to pick a suitable default timezone (those who've installed Ubuntu before should remember that it did so in 8.04 and earlier). The fact that it didn't in this case is simply a bug, namely [bug 271652]("http://launchpad.net/bugs/271652"). It's fixed in current daily builds. (And yes, you can't do a good job for all languages, but shrug. Can't win 'em all. That doesn't mean it isn't worth even trying.)

I'm not entirely sure I agree that a timeout is the right thing to do, but I'm not sure I disagree either. Compare [bug 192685]("https://launchpad.net/bugs/192685"), which might be a better approach.

---

### Post by cjwatson on 2008-09-19
If you select English and say you live in the United Kingdom, you'll already get British English translations once you reboot into the installed system. The same goes for other languages with minor local variations.

In most cases we haven't incorporated such local variants of languages into the installer, because there are some technical reasons why it's a lot more work to do this in the installer than it is to do it for the rest of the system. I don't think this is a big deal, though (and I'm a British English speaker! There simply aren't enough Americanisms in the installation process for it to be annoying). The exceptions are Chinese and Portuguese, where the differences between Simplified and Traditional Chinese and between Portuguese as spoken in Portugal and Brazilian Portuguese are much more significant than they are for local variants of other languages.

In general, rest assured that we have become pretty familiar with all the localisation issues involved, and I think we've reached a fairly reasonable compromise over the years. The timezone selection bug in Intrepid was just a glitch.

---

### Post by fballem on 2008-09-19
Probably a little off-topic (if it is, please let me know), but I have noticed a large number of 'language packs'. If there's a link that explains what they are, how they're used, and how they're built, that would be much appreciated.

Thanks,

---

### Post by olskar on 2008-09-19
> **fballem said:**
> Probably a little off-topic (if it is, please let me know), but I have noticed a large number of 'language packs'. If there's a link that explains what they are, how they're used, and how they're built, that would be much appreciated.

Thanks,

Perhaps this will help you 
[https://wiki.ubuntu.com/TranslationLifecycle](https://wiki.ubuntu.com/TranslationLifecycle)

---


---
title: "Strange characters Firefox when I Google search"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by rggavubt on 2010-07-22
I get these strange characters when I go to Google search using Firefox and Ubuntu 10.04.......see below

&#5026;&#5107;&#5069;&#5079; &#5032;&#5074; &#5027;&#5106;&#5042;&#5026;&#5024;&#5073;&#5104;&#5069;&#5079; &#5107;&#5069;&#5079; &#5024;&#5057;&#5045;&#5076;&#5061;  (These characters are on the Google search page before I search...strange characters below

&#5054;&#5069;&#5033;&#5103;&#5026; Directory &#5082;&#5054;&#5075;&#5089;&#5036;                                           search bar also)

What is going on....It reads OK using Chromium.  I can't read anything.  I am using Firefox 3.6.6.  My View....character encoding is set to :
Western(ISO-8859-1) and auto detect "on"

Installed updates this AM and google is again showing the weird characters.  English or USA is not even listed as a language choice.  I believe they were java and icetea updates.  I finally kept changing languages until I found french(I have to guess because I don't know how they say it in different languages) and chose anglaise and now right again.

---

### Post by rggavubt on 2010-07-26
I also asked this question on mozilla and someone said I should check preferences for the Google language setting.  It was not set to American.  I reset it to American and still got weird characters.  I then set it to French and then reset it to anglaise again and I'm now reading American.:popcorn:  I have never had to set my language before when I used firefox.

---

### Post by mirzmaster on 2010-08-15
I've actually been seeing the same issue, but it only appears sometimes.  I checked the Language settings of Firefox via Edit -> Preferences -> Content -> Languages.  After you hit the "Choose..." button, you will be shown the preferred Language ordering of Firefox.

Oddly enough, on that Languages screen, the only language in the list was "chrome://global/locale/intl.properties"!

To rectify the problem, I added "English [en]" to the list, and moved it above the strange entry in the ordering.  Refreshing Google now shows the correct character set.

I wonder if there is a bug open on this?

---

### Post by gyterpena on 2010-10-20
> **mirzmaster said:**
> I've actually been seeing the same issue, but it only appears sometimes.  I checked the Language settings of Firefox via Edit -> Preferences -> Content -> Languages.  After you hit the "Choose..." button, you will be shown the preferred Language ordering of Firefox.

Oddly enough, on that Languages screen, the only language in the list was "chrome://global/locale/intl.properties"!

To rectify the problem, I added "English [en]" to the list, and moved it above the strange entry in the ordering.  Refreshing Google now shows the correct character set.

I wonder if there is a bug open on this?

Thanks this worked for me.

---

### Post by abrianb on 2010-10-21
I had the same problem, I uninstalled firefox and installed firefox 4 beta. seems to not happen now.

---

### Post by efflandt on 2010-10-22
How did you end up with Firefox 3.6.6 in Lucid?  The recent default version in Lucid was 3.6.10 (recently updated in Lucid and Maverick to 3.6.11).  Unless that was a typo, maybe something else is missing.

The only languages shown under my Preferences are **English/United States [en-us]** and **English [en]**, but there is a long list of others under "Select a language to add".

Under Tools > Add-ons > Languages it lists (en), (en-AU), (en-CA), (en-GB)

I have Chromium installed, but it has nothing in its plugins directory (apparently automatically uses plugins in mozilla or firefox paths, since it uses my real 64-bit flash).

---

### Post by wensveen on 2010-10-25
> **mirzmaster said:**
> I've actually been seeing the same issue, but it only appears sometimes.  I checked the Language settings of Firefox via Edit -> Preferences -> Content -> Languages.  After you hit the "Choose..." button, you will be shown the preferred Language ordering of Firefox.

Oddly enough, on that Languages screen, the only language in the list was "chrome://global/locale/intl.properties"!

To rectify the problem, I added "English [en]" to the list, and moved it above the strange entry in the ordering.  Refreshing Google now shows the correct character set.

I wonder if there is a bug open on this?

Yes, there are bug reports open for this:
[LIST]
[*][https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/643899](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/643899)
[*][https://bugzilla.mozilla.org/show_bug.cgi?id=438031](https://bugzilla.mozilla.org/show_bug.cgi?id=438031)
[/LIST]

The best way to fix this for me was to open about:config and resetting intl.accept_languages to the default value ("en-us, en" for me).

---

### Post by jruberto on 2010-11-09
gotta say, i think this is a google issue, not any OS or browser.  i had this exact problem & checked my google search language settings & it had got reset to Afrikaans (the top item in the list).  i set it back to english & all was normal.  YMMV.

---

### Post by ShamusPatt on 2010-12-26
No, this definitely seems to be a Firefox issue.

I just ran into this issue today. I don't know why it started happening, but I did some tracing using the "Live HTTP Headers" add-on. Using the add-on, I was able to confirm that it was in fact sending this language header:

Accept-Language: chrome://global/locale/intl.properties


No web site should be expected to figure that out. It only seemed to affect Google in my case. I'm not sure why; perhaps other sites fell back on English, or the User-Agent string so it wasn't apparent,

I'm using Firefox 3.6.13 on Ubuntu Maverick.

---

### Post by rax0 on 2011-02-08
I have this problem, and I want to confirm something. Have you by any chance installed Bleachbit? if so, did it delete all the locales except English?

Bleachbit broke my Thumbnails in the past and I think it did it again with firefox.

---

### Post by abrianb on 2011-02-08
In Firefox choose edit>preferences>content>languages... click choose then from the dropdown box select English/United States [en/us] then move it to the top of the preference box. restart firefox, problem solved.

---

### Post by rax0 on 2011-02-09
Yes,  I know that. I'm trying to find the culprit.
Thanks.

---

### Post by hasanarbab on 2011-02-21
Hi all
For me it is not happening to any google search or something. everything seems to work fine except an HTML page which I wrote myself, just to teach my student, it shows all chinese kind of characters and even on yahoo mail. when I open it in Google chrome it opens perfect. 

then I tried a different thing and ran firefox as root i.e. with gksudo. Everything was just fine. my page ran perfect on that firefox opened as root.

so here is another issue which makes it a pretty much ubuntu issue. when I run firefox as myself it shows strange characters and when it is run as root it does not show those strange characters. I have tried disabling all firefox extensions, tried to change language but nothing at all is working for me except running firefox as root.

---

### Post by hasanarbab on 2011-02-21
After my last post I just thought of something and that was to to delete previous cache and then reload the page and check if language change really works.

:p:D:)

it actually did work. so what I see here that the solution is to put en-us at the top os languages list in Edit->Preferences->content->language->choose

---

### Post by cblanquer on 2011-03-18
Same issue, only on my user and for 1 PC recently upgraded from Kubuntu 9.10 to Kubuntu 10.4.
Never seen on any of my other computers on Kubuntu 10.10 or Ubuntu 10.10 nor before.
If I select a language it works ok but if no language is specified it drops to this character policy, I suspect the default is not programmed and it takes the last one instead och checking the computers language (for instance).

---


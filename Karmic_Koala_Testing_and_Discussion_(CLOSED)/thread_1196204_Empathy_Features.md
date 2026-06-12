---
title: "Empathy Features"
date: 2009-06-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cowanh00 on 2009-06-24
I'm interesting in testing out some of the features of Empathy but cannot figure out what packages I should install. 

I wanted to check out the Geolocation as discussed [here]("http://blog.pierlux.com/2009/06/15/geolocation-in-empathy-now-real/en/") and have installed all of the geoclue packages but there are no options showing after a restart of Empathy. Also I was hoping to install an Adium theme or two but again after installing the webkit package there still doesn't seem to be the option to do this!

Any help will be great! :D

---

### Post by zekopeko on 2009-06-24
what version are you running? try this daily ppa: [https://edge.launchpad.net/~amoog/+archive/empathy-daily](https://edge.launchpad.net/~amoog/+archive/empathy-daily)

---

### Post by cowanh00 on 2009-06-24
> **zekopeko said:**
> what version are you running? try this daily ppa: [https://edge.launchpad.net/~amoog/+archive/empathy-daily](https://edge.launchpad.net/~amoog/+archive/empathy-daily)

I was using the Telepathy PPA. I thought it has the latest version (2.27.3) but I'll try this other one. Thanks.

---

### Post by descendent87 on 2009-06-24
I'm running the daily ppa, with all the geoclue packages but no geolocation either, shame

---

### Post by Aries K on 2009-06-24
Hi, Empathy is looking very promising. It reminds me of Ichat. Does Empathy have sounds for send/receive ims and does it (or will it) work with Notify-OSD? Thanks in advance. :D

---

### Post by descendent87 on 2009-06-24
Yes it has sounds for sent/recieved im's and yes it supports notify-osd

---

### Post by graaant on 2009-06-24
I'm running the daily PPA. 2.27.4 but can't sign into an MSN account.
Just getting "Network error" - Anyone else getting this?

---

### Post by cowanh00 on 2009-06-25
So nobody knows how so enable Adium themes and Geolocation in Empathy?

---

### Post by nhasian on 2009-06-25
I couldnt find Adium either.  according to [this]("http://blogs.gnome.org/xclaesse/2009/06/15/empathy-adium-geolocalisation-desktop-sharing-and-file-transfer/") Empathy should have adium support as of 2.27.3, which is in the repos, and what i'm running.  I tried to follow the instructions to install a theme from [here]("http://live.gnome.org/Empathy/Themes") but there is no *Adium* choice under preferences to select a theme i've downloaded.

---

### Post by Bou on 2009-06-25
Curiously, the version in the PPA did have adium support.

---

### Post by soapytheclown on 2009-06-25
> **graaant said:**
> I'm running the daily PPA. 2.27.4 but can't sign into an MSN account.
Just getting "Network error" - Anyone else getting this?

I just double checked and my msn account signs in fine, but i have no sounds even though they are enabled, i still think empathy is very basic and not really a fan of its minimalist feel but its improved alot since i last used it lets hope the devs can

---

### Post by yelo3 on 2009-06-25
What's your preferred adium theme?

for people who can't connect to MSN: you should kill the telepathy-butterfly process and reconnect

---

### Post by moomex on 2009-06-25
> Curiously, the version in the PPA did have adium support. 

I'm running the daily PPA. 2.27.4 but but still no audium support nor geoloction.

---

### Post by descendent87 on 2009-06-25
I'm running 2.27.4 from the daily PPA and adium themes are working for me, no geolocation though

---

### Post by moomex on 2009-06-25
I updated empathy just now. Audium theme support works but no Geolocation

---

### Post by ssam on 2009-06-25
looks like geoloc has been disabled because of a dependency issue

> 
empathy (2.27.3-2ubuntu1) karmic; urgency=low

  * Merge from debian experimental, remaining changes:
    - Add Suggests on telepathy-idle
    - Bump telepathy-butterfly and telepathy-haze to recommends
  * Drop libindicate support for now
  * Drop geoloc support, dependencies not in main (yet)

[https://launchpad.net/ubuntu/+source/empathy](https://launchpad.net/ubuntu/+source/empathy)

do you have the geoclue packages installed?

---

### Post by arindom on 2009-06-25
I just updated from PPA, and for me the Adium themes are working but when I am trying to view the contacts on Map it's not working. I have booked a bug already.

---

### Post by cowanh00 on 2009-06-25
> **moomex said:**
> I updated empathy just now. Audium theme support works but no Geolocation

I can confirm Adium themes are working now! This is a nice feature. I'm looking forward to Geolocation support being enabled. One small feature I miss from Pidgin is to set a status when you open the program....

---

### Post by golusweet on 2009-06-25
> **arindom said:**
> I just updated from PPA, and for me the Adium themes are working but when I am trying to view the contacts on Map it's not working. I have booked a bug already.

yeah, Not working for me too.

Also, Adium themes support is very buggy right now. It keeps on crashing for me.

---

### Post by nhasian on 2009-06-25
someone must have heard us because as of today's empathy update from 2.27.3-1 to 2.27.3-2 the adium themes support is enabled.  I really like the [Adium Matte]("http://adiumxtras.com/index.php?a=xtras&xtra_id=4987") theme.  I also noticed on the previous version when you press the close widgit, it would use my 'close window' compiz animation and go to the system tray under that envelope icon.  I like it better now - regardless of wether you press minimize or close widgit, it uses my minimize compiz animation (magic-lamp) so you get a nice visualization showing you that Empathy is still running on the system tray.

---

### Post by cowanh00 on 2009-06-25
> **nhasian said:**
> someone must have heard us because as of today's empathy update from 2.27.3-1 to 2.27.3-2 the adium themes support is enabled.

Yay for the devs paying attention! :D

---

### Post by Staz on 2009-06-25
To confirm what arindom said, the PPA just got updated this morning with the geolocation and the adiums theme, so if you have empathy 2.27.3 from before that you will need to update (you need 2.73-2).

Don't know if it is now enabled in karmic build tough

The libnotification (the mail icon thing) was disabled in the PPA got it was buggy but the Ubuntu dev are working with upstream to fix that.

Also note that for the geolocalisation stuff to works you need a Jabber server which support PubSub (some old servers and GTalk don't). You also need some contacts which publish their location obviously ;)

Hope this helps

---

### Post by cowanh00 on 2009-06-25
> **Staz said:**
> Also note that for the geolocalisation stuff to works you need a Jabber server which support PubSub (some old servers and GTalk don't). You also need some contacts which publish their location obviously ;)

So to confirm, it is only Jabber contacts (not Gtalk) that can potentially show their location? What about MSN and the other protocols? Do any of them support PubSub?

---

### Post by Staz on 2009-06-25
> **cowanh00 said:**
> So to confirm, it is only Jabber contacts (not Gtalk) that can potentially show their location? What about MSN and the other protocols? Do any of them support PubSub?
Yes for now it's only Jabber. We are hoping Google will fix their server to respect more of the Jabber protocols. ATM if your account is on GTalk you can see the location of your contact who have published it but you cannot show your.

---

### Post by cowanh00 on 2009-06-25
> **Staz said:**
> Yes for now it's only Jabber. We are hoping Google will fix their server to respect more of the Jabber protocols. ATM if your account is on GTalk you can see the location of your contact who have published it but you cannot show your.

Thanks for the great info!

---

### Post by deathsshadow77 on 2009-06-25
yea i like adium matte too.
this is a very welcome update.

has anyone noticed that after closing a window and reopening it that chats are no longer bundled for each user but separate? I couldn't find a bug for this issue and im wondering if anyone has info on it. Same thing also happens when you look at previous conversations. Before I report a bug I just want to know whats going on with this.

---

### Post by graaant on 2009-06-25
> **yelo3 said:**
> What's your preferred adium theme?

for people who can't connect to MSN: you should kill the telepathy-butterfly process and reconnect


This didn't work for me.
I'm assuming I start up Empathy then open sysmonitor and kill telapathy-butterfly?

I just get the Network Error, then it will just sit there forever looking like it's trying to connect. Sometimes it'll disconnect my account from Pidgin but never sign into Empathy MSN :(

---

### Post by Aries K on 2009-06-26
How are you guys getting your Adium styles to work? I keep getting "not a valid style" when trying to select the Matte theme.

---

### Post by nhasian on 2009-06-26
Open the file chooser and browse to the place where you extract the theme. You have to select the folder foo.AdiumMessageStyle 

> **Aries K said:**
> How are you guys getting your Adium styles to work? I keep getting "not a valid style" when trying to select the Matte theme.

---

### Post by arindom on 2009-06-26
I have three minor problems in Empathy for which I request some help.

a) In Empathy if I click  --> View --> Contacts on a Map option, a transparent window comes up and no map was showing. Initially when the windows is loading it flashes the map for a second or less than that but then it's only a transparent window. 

I booked a [bug]("http://bugzilla.gnome.org/show_bug.cgi?id=586941") which  is closed now. As I guessed earlier, this was a Compiz issue and not an Empathy problem.

But I got report from another user that at his end the map is showing up in Compiz and there is no problem.

Later I noticed that at my end if I switch to Metacity then it's working. 

I would like to know whether I have to do anything extra to get the map working on Compiz or whether it's simply not possible.

2) I am not hearing any sound notification in Empathy. Presently I am on Alsa, is that any problem.

3) Is there any plan to show visual notification when a contact logs in / logs out/ goes idle? Something like Pidgin -> Guification.

Empathy is improving very fast, so my expectations from it has also increased. I am sure all the above can be solved.

---

### Post by Joe_Bishop on 2009-06-26
> 3) Is there any plan to show visual notification when a contact logs in / logs out/ goes idle? Something like Pidgin -> Guification.

check the settings, it's already here.

---

### Post by Aries K on 2009-06-26
> **nhasian said:**
> Open the file chooser and browse to the place where you extract the theme. You have to select the folder foo.AdiumMessageStyle

That's what I did and I still get the "Not a valid Adium style" message. I even have webkit installed. I am using the latest version from the daily PPA. Am I doing something wrong? Thanks again.

---

### Post by Joe_Bishop on 2009-06-26
> **Aries K said:**
> That's what I did and I still get the "Not a valid Adium style" message. I even have webkit installed. I am using the latest version from the daily PPA. Am I doing something wrong? Thanks again.
Think yourself. It's obviously your mistake.

---

### Post by Bou on 2009-06-26
> **arindom said:**
> 3) Is there any plan to show visual notification when a contact logs in / logs out/ goes idle? Something like Pidgin -> Guification.

I have filed a request about that, please support it:

[http://bugzilla.gnome.org/show_bug.cgi?id=587019](http://bugzilla.gnome.org/show_bug.cgi?id=587019)

---

### Post by arindom on 2009-06-26
> **Aries K said:**
> That's what I did and I still get the "Not a valid Adium style" message. I even have webkit installed. I am using the latest version from the daily PPA. Am I doing something wrong? Thanks again.

Hi Aries,

This is what I did. Here are the steps :
a) First download the Adium Theme. I tried with "adium_matte" theme. Then unzip it in a directory.
b) In Empathy, go to Edit --> Preference --> Themes.
c) Choose Chat Theme as Adium. [ I think upto here it's no problem at your end].
d) Now select the theme directory where you have extracted the theme earlier in setp a).
e) No go to the this directory : Adium Matte.AdiumMessageStyle.
f) Here you should find a directory called "Contents"
g) Now click Open button. 

Please note the catch is don't go inside contents directory, just point your selector on contents and click open button.

Now it should work for you too. 

I was facing the same problem yesterday but thanks to another user (tgapraveen), I got this solved.

---

### Post by tgpraveen on 2009-06-26
> **Bou said:**
> I have filed a request about that, please support it:

[http://bugzilla.gnome.org/show_bug.cgi?id=587019](http://bugzilla.gnome.org/show_bug.cgi?id=587019)
 known bug and i think it is already added in git master
so should be available for .4

---

### Post by arindom on 2009-06-26
> **Bou said:**
> I have filed a request about that, please support it:

[http://bugzilla.gnome.org/show_bug.cgi?id=587019](http://bugzilla.gnome.org/show_bug.cgi?id=587019)

Supported. Thanks for the link. 

I have added a few lines too, I hope I can add my wish in the ticket.

---

### Post by Aries K on 2009-06-26
> **arindom said:**
> Hi Aries,

This is what I did. Here are the steps :
a) First download the Adium Theme. I tried with "adium_matte" theme. Then unzip it in a directory.
b) In Empathy, go to Edit --> Preference --> Themes.
c) Choose Chat Theme as Adium. [ I think upto here it's no problem at your end].
d) Now select the theme directory where you have extracted the theme earlier in setp a).
e) No go to the this directory : Adium Matte.AdiumMessageStyle.
f) Here you should find a directory called "Contents"
g) Now click Open button. 

Please note the catch is don't go inside contents directory, just point your selector on contents and click open button.

Now it should work for you too. 

I was facing the same problem yesterday but thanks to another user (tgapraveen), I got this solved.

Thank you so much, it's working great now! :D

---

### Post by chriswyatt on 2009-06-26
I found I had to go inside the folder when selecting the Adium theme, they should change that behaviour, the opening dialogue is a bit buggy in Ubuntu.  I also have problems with it when extracting using file-roller, I have to click on a file or a folder otherwise the Extract button doesn't work.

---

### Post by Merkaba_ZA on 2009-06-27
Loving Empathy so far but for some reason I'm not getting notifications of contacts logging on and no sound effects play even though they are enabled in Empathy itself. Regarding the notifications, I do get notifications of messages received, just not when contacts log on.  Any ideas?

---

### Post by MacUntu on 2009-06-27
How can I change the icon theme? Is it normal that the contact info for ICQ contacts is... spartanic?

---

### Post by tgpraveen on 2009-06-27
> **Merkaba_ZA said:**
> Loving Empathy so far but for some reason I'm not getting notifications of contacts logging on and no sound effects play even though they are enabled in Empathy itself. Regarding the notifications, I do get notifications of messages received, just not when contacts log on.  Any ideas?
the notification for login/logout is already added. if u compile from git u will get it else wait for 2.27.4

---

### Post by Merkaba_ZA on 2009-06-27
Thanks.  Good to know :)

---

### Post by jfanaian on 2009-06-28
Empathy is great! And I have to admit, this PPA makes it so much easier... I was trying to get Adium themes working by compiling it myself but couldn't.

Thanks for all the work! :)

---

### Post by aamukahvi on 2009-07-15
Just got Empathy in the latest updates (i.e. with ubuntu-desktop).

---

### Post by nhasian on 2009-07-15
just in the nick of time.  Empathy 2.27.4 is out and should find it way to the repository soon.

It has a bunch of [bug fixes]("http://ftp.acc.umu.se/pub/GNOME/sources/empathy/2.27/empathy-2.27.4.news")

---

### Post by rockin_goliath on 2009-07-16
I have a few questions about Empathy development:

[LIST=1]
[*]How is video chat coming along?
[*]Does video chat work with the Gmail video chat interface yet?
[*]Can one choose audio and video devices within Empathy now?
[/LIST]

I am sooooooooo looking forward to dumping Skype for good.

---

### Post by Changturkey on 2009-07-16
How "good" is the MSN support?

---

### Post by yelo3 on 2009-07-16
definitely not good. I suggest you to keep pidgin if you use msn

---

### Post by Nerd_bloke on 2009-07-16
> **yelo3 said:**
> definitely not good. I suggest you to keep pidgin if you use msn

The backend to Empathy's MSN protocol support in Karmic is telepathy-haze, this uses libpurple i.e. exactly the same as pidgin.

Telepathy-butterfly will be re-enabled in the future (karmic+1?), after its underlying papyon branch has MSN webcam call support.

---

### Post by Staz on 2009-07-16
> **rockin_goliath said:**
> I have a few questions about Empathy development:

[LIST=1]
[*]How is video chat coming along?
[*]Does video chat work with the Gmail video chat interface yet?
[*]Can one choose audio and video devices within Empathy now?
[/LIST]

I am sooooooooo looking forward to dumping Skype for good.

  1. It is working right now for Jabber/XMPP thought I don't know if there are compatibles clients a part from GTalk and from Empathy to Empathy.

  2. It should be working although I heard there is still some minor bugs which cause it not to work in some cases. Also there is still the codec issue : Gmail use some proprietary codec than Ubuntu can't ship by default.

 3.  You can choose the devices in Gnome sound property (the device under Audio Conferencing) and gstreamer-properties, Empathy will use theses settings.
 3.

---

### Post by Staz on 2009-07-16
> **Merkaba_ZA said:**
> Loving Empathy so far but for some reason I'm not getting notifications of contacts logging on and no sound effects play even though they are enabled in Empathy itself.
For the sound notification check if you they are enabled in gnome-sound-properties and if you have a proper sound theme installed which contain the corresponding sound

---

### Post by BCurtisWX on 2009-07-16
thats not how you get audio for empathy to work.... next suggestion?

---

### Post by Changturkey on 2009-07-16
> **Nerd_bloke said:**
> The backend to Empathy's MSN protocol support in Karmic is telepathy-haze, this uses libpurple i.e. exactly the same as pidgin.

Telepathy-butterfly will be re-enabled in the future (karmic+1?), after its underlying papyon branch has MSN webcam call support.

Karmic +1? Aw man.

---

### Post by Staz on 2009-07-17
> **BCurtisWX said:**
> thats not how you get audio for empathy to work.... next suggestion?
by audio you mean the notificiations or  the voice over IP ?(if everything fail, blame PulseAudio it's easy ;))

For sound notification apparently the default ubuntu sound theme contain only the phone-incoming-call sound, you need to install this one :
[http://people.freedesktop.org/~mccann/dist/sound-theme-freedesktop-0.2.tar.bz2](http://people.freedesktop.org/~mccann/dist/sound-theme-freedesktop-0.2.tar.bz2) to have all the required sounds

---

### Post by BCurtisWX on 2009-07-17
[https://bugs.edge.launchpad.net/ubuntu/+source/empathy/+bug/400485](https://bugs.edge.launchpad.net/ubuntu/+source/empathy/+bug/400485)

I've filed a bug to try to get this fixed before karmic is released.

---

### Post by zekopeko on 2009-07-17
> **Changturkey said:**
> Karmic +1? Aw man.

Go go Power Package Archives!!!

---

### Post by Staz on 2009-07-17
> **BCurtisWX said:**
> [https://bugs.edge.launchpad.net/ubuntu/+source/empathy/+bug/400485](https://bugs.edge.launchpad.net/ubuntu/+source/empathy/+bug/400485)

I've filed a bug to try to get this fixed before karmic is released.
silly me, I didn't notice you were the one who asked about this on IRC, I nearly linked you to your own bug report ^^;

---

### Post by BCurtisWX on 2009-07-17
> **Staz said:**
> silly me, I didn't notice you were the one who asked about this on IRC, I nearly linked you to your own bug report ^^;

that would have been priceless

---

### Post by B Crowther on 2009-08-06
With effect from an update this morning, the Adium themes have been disabled, which is really, really annoying as I had edited the css for the one I was using to get it as I preferred.

Oh well, these things happen when you play with developing software.

Later: Got the adium theme working again, after the option disapeared from the preferences dialog when program was updated to 2.27.5 this morning.

Went to System Tools>Configuration Editor>Apps>Empathy>Conversation and edited the theme name to read adium.

This seems to persist through a reboot fairly reliably, but if you are silly enough to open the "Themes" tab in Empathy Preferences then it will immediately default back to one of the blah-looking themes that come standard.:D

---

### Post by B Crowther on 2009-08-06
Got the adium theme working again, before I found out I could edit my previous message, and I can't delete this message - damn!

---

### Post by philinux on 2009-08-06
Shame Empathy does not do an IRC client.

[edit] [telepathy-idle] should be installed by default I reckon.

---

### Post by Aries K on 2009-08-07
> **Staz said:**
> by audio you mean the notificiations or  the voice over IP ?(if everything fail, blame PulseAudio it's easy ;))

For sound notification apparently the default ubuntu sound theme contain only the phone-incoming-call sound, you need to install this one :
[http://people.freedesktop.org/~mccann/dist/sound-theme-freedesktop-0.2.tar.bz2](http://people.freedesktop.org/~mccann/dist/sound-theme-freedesktop-0.2.tar.bz2) to have all the required sounds

Where do you extract that to? It would be nice to have notification sounds. Thanks in advance.

---

### Post by cheleb on 2009-08-07
> **Aries K said:**
> Where do you extract that to?

Just fire up Synaptic and install the sound-theme-freedesktop package. It's in the repositories

---

### Post by Aries K on 2009-08-07
> **cheleb said:**
> Just fire up Synaptic and install the sound-theme-freedesktop package. It's in the repositories

Thanks but I still don't have sound in Empathy. :(

---

### Post by cheleb on 2009-08-08
> **Aries K said:**
> Thanks but I still don't have sound in Empathy. :(

Be sure to enable sound notifications in the preferences.
That worked here. See attached screenshot.

---

### Post by Changturkey on 2009-08-08
Does Empathy do Facebook chat?

---

### Post by Aries K on 2009-08-08
> **cheleb said:**
> Be sure to enable sound notifications in the preferences.
That worked here. See attached screenshot.

Yep that was the first thing I've done before getting the free-desktop package. Maybe it's pulseaudio?

---

### Post by cheleb on 2009-08-08
> **Aries K said:**
> Yep that was the first thing I've done before getting the free-desktop package. Maybe it's pulseaudio?

I totally forgot that you have to enable the new fdo sounds in the gnome sound preferences. Change the Sound Theme to "Default". That should do the trick.

---

### Post by Aries K on 2009-08-09
> **cheleb said:**
> I totally forgot that you have to enable the new fdo sounds in the gnome sound preferences. Change the Sound Theme to "Default". That should do the trick.

Thanks, you are so helpful by going out the way to upload pictures. That did the trick for the most part. The incoming chat sounds are working now but the send sounds don't but that's no biggie. I find it cool how they are the same sounds as Kopete lol.

---

### Post by Staz on 2009-08-09
Not out of the box but I think there was a tutorial to make it works

---

### Post by oOarthurOo on 2009-08-09
If empathy doesn't do IRC its of no use to me. I saw a report online from a year ago saying it was enabled. Am I missing something? Currently using the version in Karmic.

---

### Post by steeleyuk on 2009-08-09
It does IRC with telepathy-idle installed.

---

### Post by oOarthurOo on 2009-08-09
Thanks steeley, I can now configure my irc account. Now if only I could figure out how to join a room! Any more tips?

---

### Post by oOarthurOo on 2009-08-09
To join #ubuntu, you have to switch the default server to 'freenode'. Then close the window that opens and click on room, to join a room. You can't just type "/join #ubuntu" in the freenode window. A little different from pidgin. :)

---

### Post by gunbladeiv on 2009-09-14
I've been using daily ppa and still cant enable the adium theme support till now.  Here is the package which installed on my laptop. Do you guys have any idea what package i possibly missed? 

```
ii  empathy                                                                 2.27.92.20090913101736-0daily1             High-level library and user-interface for Te
ii  libempathy-common                                                       2.27.92.20090913101736-0daily1             High-level library and user-interface for Te
ii  libempathy-gtk-common                                                   2.27.92.20090913101736-0daily1             High-level library and user-interface for Te
rc  libempathy-gtk19                                                        2.26.1-1ubuntu1                            High-level library and user-interface for Te
rc  libempathy-gtk25                                                        2.27.5-0ubuntu1                            High-level library and user-interface for Te
ii  libempathy-gtk27                                                        2.27.92.20090913101736-0daily1             High-level library and user-interface for Te
rc  libempathy-gtk28                                                        2.27.92-1ubuntu1                           High-level library and user-interface for Te
rc  libempathy23                                                            2.26.1-1ubuntu1                            High-level library and user-interface for Te
rc  libempathy27                                                            2.27.5-0ubuntu1                            High-level library and user-interface for Te
ii  libempathy29                                                            2.27.92.20090913101736-0daily1             High-level library and user-interface for Te
rc  libempathy30                                                            2.27.92-1ubuntu1                           High-level library and user-interface for Te
ii  libwebkit-1.0-1                                                         1.0.1-4                                    Web content engine library for Gtk+
ii  libwebkit-1.0-2                                                         1.1.13-1ubuntu1                            Web content engine library for Gtk+
ii  libwebkit-1.0-common                                                    1.1.13-1ubuntu1                            Web content engine library for Gtk+ - data f
ii  libwebkit-dev                                                           1.1.13-1ubuntu1                            Web content engine library for Gtk+ - Develo
ii  libtelepathy-farsight0                                                  0.0.11.20090913102206-0daily1              Glue library between telepathy and farsight2
ii  libtelepathy-glib0                                                      0.7.37.20090913101934-0daily1              Telepathy framework - GLib library
rc  libtelepathy2                                                           0.3.3-2                                    Telepathy framework - old GLib library
ii  telepathy-gabble                                                        0.9.0.20090905230139-0daily1               Jabber/XMPP connection manager
ii  telepathy-idle                                                          0.1.4.20090913102110-0daily1               IRC connection manager for Telepathy
ii  telepathy-mission-control-5                                             5.2.2-1                                    management daemon for Telepathy real-time co
ii  telepathy-salut                                                         0.3.9-1ubuntu1                             Link-local XMPP connection manager for the T
ii  geoclue                                                                 0.11.1-5                                   Geographic information framework
ii  geoclue-hostip                                                          0.11.1-5                                   Position server for GeoClue (hostip)
ii  geoclue-localnet                                                        0.11.1-5                                   Position server for GeoClue (GPS)
ii  geoclue-manual                                                          0.11.1-5                                   Position server for GeoClue (manual)
ii  geoclue-yahoo                                                           0.11.1-5                                   Map and geocode server for GeoClue (Yahoo)
ii  libgeoclue0                                                             0.11.1-5                                   C API for GeoClue

```

---

### Post by Aries K on 2009-09-14
> **gunbladeiv said:**
> I've been using daily ppa and still cant enable the adium theme support till now.  Here is the package which installed on my laptop. Do you guys have any idea what package i possibly missed? 

```
ii  empathy                                                                 2.27.92.20090913101736-0daily1             High-level library and user-interface for Te
ii  libempathy-common                                                       2.27.92.20090913101736-0daily1             High-level library and user-interface for Te
ii  libempathy-gtk-common                                                   2.27.92.20090913101736-0daily1             High-level library and user-interface for Te
rc  libempathy-gtk19                                                        2.26.1-1ubuntu1                            High-level library and user-interface for Te
rc  libempathy-gtk25                                                        2.27.5-0ubuntu1                            High-level library and user-interface for Te
ii  libempathy-gtk27                                                        2.27.92.20090913101736-0daily1             High-level library and user-interface for Te
rc  libempathy-gtk28                                                        2.27.92-1ubuntu1                           High-level library and user-interface for Te
rc  libempathy23                                                            2.26.1-1ubuntu1                            High-level library and user-interface for Te
rc  libempathy27                                                            2.27.5-0ubuntu1                            High-level library and user-interface for Te
ii  libempathy29                                                            2.27.92.20090913101736-0daily1             High-level library and user-interface for Te
rc  libempathy30                                                            2.27.92-1ubuntu1                           High-level library and user-interface for Te
ii  libwebkit-1.0-1                                                         1.0.1-4                                    Web content engine library for Gtk+
ii  libwebkit-1.0-2                                                         1.1.13-1ubuntu1                            Web content engine library for Gtk+
ii  libwebkit-1.0-common                                                    1.1.13-1ubuntu1                            Web content engine library for Gtk+ - data f
ii  libwebkit-dev                                                           1.1.13-1ubuntu1                            Web content engine library for Gtk+ - Develo
ii  libtelepathy-farsight0                                                  0.0.11.20090913102206-0daily1              Glue library between telepathy and farsight2
ii  libtelepathy-glib0                                                      0.7.37.20090913101934-0daily1              Telepathy framework - GLib library
rc  libtelepathy2                                                           0.3.3-2                                    Telepathy framework - old GLib library
ii  telepathy-gabble                                                        0.9.0.20090905230139-0daily1               Jabber/XMPP connection manager
ii  telepathy-idle                                                          0.1.4.20090913102110-0daily1               IRC connection manager for Telepathy
ii  telepathy-mission-control-5                                             5.2.2-1                                    management daemon for Telepathy real-time co
ii  telepathy-salut                                                         0.3.9-1ubuntu1                             Link-local XMPP connection manager for the T
ii  geoclue                                                                 0.11.1-5                                   Geographic information framework
ii  geoclue-hostip                                                          0.11.1-5                                   Position server for GeoClue (hostip)
ii  geoclue-localnet                                                        0.11.1-5                                   Position server for GeoClue (GPS)
ii  geoclue-manual                                                          0.11.1-5                                   Position server for GeoClue (manual)
ii  geoclue-yahoo                                                           0.11.1-5                                   Map and geocode server for GeoClue (Yahoo)
ii  libgeoclue0                                                             0.11.1-5                                   C API for GeoClue

```


Extract the tarball to ~/.local/share/adium/message-styles/*.AdiumMessageStyle That should do the trick.

---

### Post by soapytheclown on 2009-09-14
has anyone got facebook chat working with the latest versions i had it working before but after an update a while back it stopped

---

### Post by gunbladeiv on 2009-09-15
> **Aries K said:**
> Extract the tarball to ~/.local/share/adium/message-styles/*.AdiumMessageStyle That should do the trick.

thanks Aries, yeah that'll do the trick. Now i got the adium matte loaded. XD
Geolocation also installed. :lolflag:

---

### Post by Aries K on 2009-09-15
> **gunbladeiv said:**
> thanks Aries, yeah that'll do the trick. Now i got the adium matte loaded. XD
Geolocation also installed. :lolflag:

Awesome, glad you got it working. I'm in love with the Adium Matte theme, it is very I-chat esque.

---

### Post by bash on 2009-09-15
Next update of Empathy will feature audio/video chat, offline messages and file transfer for MSN.

See here:
[http://cass.no-ip.com/~cassidy/blog/index.php/post/2009/09/14/MSN-audio/video-chat-in-Telepathy](http://cass.no-ip.com/~cassidy/blog/index.php/post/2009/09/14/MSN-audio/video-chat-in-Telepathy)

---

### Post by Aries K on 2009-09-15
> **bash said:**
> Next update of Empathy will feature audio/video chat, offline messages and file transfer for MSN.

See here:
[http://cass.no-ip.com/~cassidy/blog/index.php/post/2009/09/14/MSN-audio/video-chat-in-Telepathy](http://cass.no-ip.com/~cassidy/blog/index.php/post/2009/09/14/MSN-audio/video-chat-in-Telepathy)

Very nice, props to the devs. :popcorn:

---

### Post by gunbladeiv on 2009-09-16
I hope that empathy will have video call work on gtalk.  I tested out voice call on gtalk and it work flawlessly. Kudos to all devs team on this.  Empathy really improve a lot in the past 2-3 months.

---


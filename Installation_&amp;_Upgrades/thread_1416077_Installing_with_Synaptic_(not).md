---
title: "Installing with Synaptic (not)"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by paulemony on 2010-02-25
I thought Synaptic installed programs, no further action necessary, but apparently not. I downloaded get-iplayer but it doesn't appear in Sound & Video nor any other menu. If I add it in Main Menu (command: get-iplayer)& then try to open it nothing happens. What does it want from me?

---

### Post by Scarfnoogan on 2010-02-25
did you restart/log out-in? sometimes I find I have to for it to work

---

### Post by davec64 on 2010-02-25
HI,

get-iplayer is a command line programmme, so to use it you need to open a terminal and at the prompt type:

```
get_iplyer
```

This will then connect and download the full list of availale downloads. To search for by a specific word, e.g. for "QI. type:

```
get_iplayer qi
```

This will return a list of any programmes with "QI" in it's title. on the left of the avaiable downloads is the PID (a number). So to download a specific programme to your home folder (where the 1234 below is the PID), type:

```
get_iplayer --get 1234
```

That's just a few very basic commands to get you started, but if you visit the get-iplayer site, the full list of commands is available.

Don't be frightened that it is a command line programme as it is actually extremely good and powerful, I use it alot!  :)


EDIT:
Just a thought, I don't know if it works outside the UK, but saying that, no harm in testing!
The BBC Iplayer web site does block access from outside the UK I believe, whether or not get_iplayer is affected. I don't know! :)

---

### Post by paulemony on 2010-02-26
Tried that but 2 problems; I ended up with this but then what?:

Matches:
721:	The Politics Show South East - 21/02/2010, BBC One, Factual,News,Politics,TV, default,

INFO: 1 Matching Programmes

After which nothing happened, and anyway even if it did it was a laborious way to find & start playing a tv programme. 

My main point was that I thought that if I installed something with   
Synaptic then it should surely work out-of the-box?

---

### Post by davec64 on 2010-02-26
Nope, Synaptic installs everything from library's to GUI programmes to command line programs, It's a GUI programme for the terminal command apt.

If you want to install just programmes that appear in your applications menu, using the Ubuntu Software Centre is a better option.

By the way, you were nearly there with get_iplayer, from what you listed in your post then next command would be:

```
get_iplayer --get 721
```

Get_iplayer, by default only downloads the Iphone version of a programme. It was designed so people with Iphones could watch programmes at there leisure on their Iphones when not in a wifi supported area. The quality is good enough to watch on a PC as well (I think! :) )

If you just want to watch TV programmes, why not just install the BBC Iplayer programme from their site?

[http://www.bbc.co.uk/iplayer/install/]("http://www.bbc.co.uk/iplayer/install/")

Then when you open up Iplayer in a web browser, beneath the viewing window you'll have a download option which you can then watch at a later date from the Iplayer app.

Hope that helps!   :)

---

### Post by paulemony on 2010-02-26
I tried downloading from BBC (Linux version)but when I click on Play it doesn't.
To start from the beginning,if I want to use Iplayer in ubuntu, exactly how do I do it? Nothing I try works!

---

### Post by paulemony on 2010-02-26
!

---

### Post by davec64 on 2010-02-26
Follow the link I posted. It will take you to the install page.
There's a grey bar about a third of the way down the page to start with, after a few seconds this will change and tell you you need to install Adobe Air. Click ok and follow the instructions to install it.
When you return to the page after installing Adobe Air (refresh it) you'll then get the option to install BBC IPlayer Desktop instead.

Now when you visit the BBC web site, when you click download it should download to the Desktop App.

For the BBC web site version (watching live), have you got adobe flash installed? 

If the above doesn't work post back with the error messages and I'll try and help. :)

Just a thought, your install of Ubuntu is it the 32bit or the 64bit? If it's the 64bit you will need some 32bit libraries to get Adobe Air working.


EDIT:
Don't worry about Flash, I see you've already got it install, but you need the Desktop App for the download to work. When you've got it installed you'll find it under the Applications menu somewhere and it looks like the attachment.

---

### Post by linuxcentre on 2010-02-26
> **davec64 said:**
> Get_iplayer, by default only downloads the Iphone version of a programme.

That's not quite the case;

get_iplayer will record any flash based stream from iPlayer also (and by default) as long as you have the flvstreamer dependency installed. It even record the HD streams :-)

There is a bug in the synaptic version (2.41) which means that the iPhone stream is broken since the BBC changed their website last year. The one on the get_iplayer website works fine.

I suggest just getting the one from [http://linuxcentre.net/](http://linuxcentre.net/) download page and follow the very simple installation instructions. There is even a deb there...

I'd also recommend manually getting flvstreamer (links from same website) because the later version is MUCH more reliable.

---

### Post by davec64 on 2010-02-27
Your right, Iplayer will record any flash based stream, but by default it will select the iphone version if it is available first. If it's unavailable it wil try other availbe flash streams (assuming you have flvstreamer installed). That said, there's nothing stopping you from changing the default action to your own preference!

Great point re: the bug in the repository version. I never come across it as I always run the latest version from the web site. This is the quickest place to get a working version when the BBC change things (as they do occasionally!)

---

### Post by paulemony on 2010-02-27
For the record I'm running a Wubi Ubuntu 9.1 installation. which I take to be 64bit. I tried get-iplayer using terminal installation & see that it downloads rather than streams & isn't actually a player in its own right (correct me if I'm wrong) but the tv programmes can be played on movie player. I also tried reinstalling BBC Iplayer but the Adobe Air installation option didn't appear & when I tracked the instructions down I'm afraid my eyes soon glazed over! Maybe I'll try downloading the Windows version & use Wine (yes I know I also have Windows anyway & could just use that but the object of the exercise is to get to grips with Linux). Anyway thanks for all suggestions.

---

### Post by paulemony on 2010-02-27
OK, fixed it, answer was simple (as of course are all computer problems in the end), took BBC's advice to save rather than open when (re)installing Iplayer & then open afterwards (or it might have been retrying the Adobe Air installer)but either way both Iplayer and get-iplayer (now redundant?)seem to be working.

---

### Post by davec64 on 2010-02-27
Glad it works!
It's strange how sometimes it just all falls into place and your up and running!

Have fun playing!

---


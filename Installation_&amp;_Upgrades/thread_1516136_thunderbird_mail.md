---
title: "thunderbird mail"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by shipinomore on 2010-06-23
trying to install Thunderbird mail.
used kpackagekit to try and find it but no luck. how can I install the latest version?
I tried to install Kmail but it seems to hang up and never get the account set up.
Larry

---

### Post by ashwinrao on 2010-06-23
First download and install Ubuntu Tweak by referring to [this]("http://ubuntu-tweak.com/downloads/") link. After that, you can find all the necessary packages easily including Thunderbird :p

---

### Post by Bucky Ball on 2010-06-23
You open a search engine, search for Mozilla Thunderbird, click the mouse a few times and end up here: 

[http://www.mozilla.com/en-US/products/](http://www.mozilla.com/en-US/products/)

Scroll to Thunderbird and click on it. Download, install. 

Install Ubuntu Tweak??

---

### Post by shipinomore on 2010-06-23
thank you. I will try again to do a tar install. I am somewhat new to ubuntu and very fuzzy on installs.
I also did the tweak thing and added to other souurces.
Larry

---

### Post by Thelasko on 2010-06-23
Am I missing something?  What's wrong with "sudo apt-get install mozilla-thunderbird"?

---

### Post by shipinomore on 2010-06-23
THELASKO

I did the apt-get and it came back and said that I should use thunderbird and so I did sudo apt-get install thunderbird and all went ok.
I think perhaps it was because I had started the tar file in terminal and had got as far as starting to set up my account and then lost the screen I was on by closing the terminal window which had created the imput screen.
Thank You
Larry

---

### Post by shipinomore on 2010-06-23
ashwinrao
I did put the tweak into the site thru the terminal.
not familuar with hou it works.
when using kpackagekit will it allow for more programs to come up to install?
Larry

---

### Post by Thelasko on 2010-06-23
> **shipinomore said:**
> THELASKO

I did the apt-get and it came back and said that I should use thunderbird and so I did sudo apt-get install thunderbird and all went ok.

I must have gotten the name wrong.

[You might find this page helpful.]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by shipinomore on 2010-06-23
thank you for your help and tips.
Larry

---

### Post by shipinomore on 2010-06-23
well after all the trouble of getting it installed.
I waited for hours for it to download my old e mail.
no errors just that dumb cursor going round and round.
so much for thunderbird on Kubuntu!
Larry

---

### Post by Thelasko on 2010-06-23
> **shipinomore said:**
> well after all the trouble of getting it installed.
I waited for hours for it to download my old e mail.
no errors just that dumb cursor going round and round.
so much for thunderbird on Kubuntu!
Larry

Are you sure you have it configured correctly?  Did you use the correct ports and account settings?

Your email provider should be able to provide you with the correct settings.

---

### Post by shipinomore on 2010-06-23
yes I have mail.comcast.net
and smtp.comcast.net
and it requires authorization and the port is 587
evolution works
couldn't get kmail to work with Kubuntu
thanks for asking.
the only thing more frustrating is wine.
Larry

---

### Post by Thelasko on 2010-06-23
> **shipinomore said:**
> the only thing more frustrating is wine.

Sorry to hear Thunderbird didn't work out.

As far as Wine is concerned, my experience is that most people make the mistake of installing DirectX.  Wine comes with it's own DirectX and installing it breaks Wine.  If you want to start over in Wine, you need to delete the .wine folder in your home folder. (press ctrl + h to see it)

[Here are some more helpful hints with Wine.]("http://ubuntuforums.org/showthread.php?t=885111")

---

### Post by shipinomore on 2010-06-23
here is another one. I just installed Thunderbird on Ubuntu. all went well
I set up mail.comcast.net and when i went in to check the server it showed
pop3.comcast.net and you cannot change that. if you set up again it says the server is already there.
thanks for the tip on wine. I am a diabetic and am wanting to get some software by bayer to run in wine. it installs ok but is missing a odbc that is a dll that has to do with database creation.
I also use crossover which is taboo with some in wine.
i can get them to install down to where you have to connect the usb cable to install drivers to connect to the meter.
however wine does not come back with new device found etc. so you can insert the cd to install the drivers.
but I won't give up 
Larry

---

### Post by Thelasko on 2010-06-23
I'm betting that pop3 setting looks correct.  You probably need to check a "this server requires authentication" etc. box somewhere.

For your glucose meter, that software is probably pretty specialized.  There might not be many people using it in Wine.  Try searching the [Wine Appdb]("http://appdb.winehq.org/") (search box is in the upper right corner) to see if anyone else has it working.

---

### Post by shipinomore on 2010-06-23
been there done that. Glucofacts Deluxe is there in the list but will not run. I even signed up for being an advocate with Crossover and it seems if you want to donate lots of money they will move it up the ladder to be worked on.

---

### Post by bondo101 on 2010-06-23
Make sure that you have the correct port nos and copy everything from Outlook if you have it. I had problems also untill I corrected the port nos and pop and smtp. otherwise your cursor will spin forever. I gqve up on Evolution i don't think the server connects well with it Att sucks. :p

---

### Post by Thelasko on 2010-06-23
Well, I found a list of [open source options.]("http://osdir.com/ml/debian.devel.medical/2004-03/msg00006.html")  Unfortunately, I haven't been able to find any of them in the repositories.  The best option seems to be [Insulin Buddy.]("http://sourceforge.net/projects/insbuddy/files/")  Unfortunately, you will have to compile it from source.

[Here's how you do that.]("https://help.ubuntu.com/community/CompilingEasyHowTo")

---

### Post by shipinomore on 2010-06-23
Hi Bondo will I know that port 587 on the smtp is correct will have to re verify the incoming as eithe 10 110
but it really a head scratcher wondering why it won't work.
glad i got Incredimail on the other system.

---

### Post by Thelasko on 2010-06-23
> **shipinomore said:**
> Hi Bondo will I know that port 587 on the smtp is correct will have to re verify the incoming as eithe 10 110
but it really a head scratcher wondering why it won't work.
glad i got Incredimail on the other system.

Try incoming port as 995.  That's the standard POP3 port for encrypted traffic.

---

### Post by shipinomore on 2010-06-23
OK I will try that but 995 I believe I saw was with g-mail.
Comcast here in MN said to use server requires authorization checked and to make the port 587.

---

### Post by Thelasko on 2010-06-23
> **shipinomore said:**
> Comcast here in MN said to use server requires authorization checked and to make the port 587.

That's for sending mail only.  You need another port to receive mail.

P.S. 110 is to receive unencrypted mail.  Most mail providers have stopped forwarding unencrypted traffic for security reasons.

---

### Post by kevinanchi on 2010-06-24
I have configured 6 mail Ids on thunderbird but only one mail id gets mails and also i am not able to send any mail, what could be the problem???

---

### Post by shipinomore on 2010-06-24
I did file a bug report. I have two accounts and the second one went just fine with g-mail and downloaded all of my folders that I had set up.
my primary account still will not download. once it showed downloading 427 to trash? the number was correct but nothing showed up anywhere.
right now I am using evolution.
good luck
Larry

---

### Post by ashwinrao on 2010-06-24
Larry, sorry for the late reply. I thought you were using Ubuntu(GNOME). Hence, I have suggested to install Ubuntu Tweak using which you can install many applications easily. I have not tried it in Kubuntu as I'm using GNOME.

---

### Post by shipinomore on 2010-06-24
no I was using Gnome on Ubuntu 10.04
KDE drives me crazy with the cursor losing icons and things closing. old age I guess.
I will look into the tweak thing tomorrow.
will that appear under applications?
Larry

---

### Post by Bucky Ball on 2010-06-24
> **kevinanchi said:**
> I have configured 6 mail Ids on thunderbird but only one mail id gets mails and also i am not able to send any mail, what could be the problem???

Please start a separate thread describing your problem and giving as much detail about your software as possible. You will get more help that way; this way just makes crossed wires. ;)

---


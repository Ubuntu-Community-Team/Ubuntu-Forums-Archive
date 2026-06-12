---
title: "JACK audio problem"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by d-signet on 2010-04-06
I've installed the 64-bit beta1 on 3 different machines over the last couple of days and had the same problem starting JACK on all of them.

MESSAGES windows shows : 


 p, li { white-space: pre-wrap; }  [COLOR=#999999]23:34:35.296 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]23:34:35.426 Statistics reset.[/COLOR]
 [COLOR=#66CC99]23:34:35.614 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]23:34:35.917 ALSA connection change.[/COLOR]
 [COLOR=#999999]23:34:37.824 Startup script...[/COLOR]
 [COLOR=#990099]23:34:37.826 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]23:34:38.235 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]23:34:38.235 JACK is starting...[/COLOR]
 [COLOR=#990099]23:34:38.236 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n3[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
 [COLOR=#999999]23:34:38.250 JACK was started with PID=1984.[/COLOR]
 Please check your /etc/security/limits.conf for the following lines
 and correct/add them:
   @audio          -       rtprio          100
   @audio          -       nice            -10
 After applying these changes, please re-login in order for them to take effect.
 You don't appear to have a sane system configuration. It is very likely that you
 encounter xruns. Please apply all the above mentioned changes and start jack again!
 [COLOR=#999999]23:34:38.290 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]23:34:38.291 Post-shutdown script...[/COLOR]
 [COLOR=#990099]23:34:38.291 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]23:34:38.739 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]23:34:40.394 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]


I've made the change suggested on all 3 machines in the vain hope that it might work ( sudo editing the limits.conf ) but get the same problem.
The install seems to default to using realtime kernel whether you choose it in the install process or not - system is still using the default kernel - have unchecked REALTIME from the qjackctl SETUP window - logged off and on again - same error. thought it wsa just me and my machine and i'd iron it out tonight but then had the same problem on 2 other machines at work so thinking its a default config bug

---

### Post by Sevenmead on 2010-04-07
Same here... I get two errors

 p, li { white-space: pre-wrap; }  cannot continue execution of the processing graph (Bad file descriptor)
 jackd: no process found

I'm trying to run Internet DJ Console... and it needs jack.. 

I hate asking questions that should be easy to find and I have tried...

But what is Jack. What is it doing?  Why does the audio that works normal ystop as soon as it is open?

---

### Post by d-signet on 2010-04-07
@sevenmead - have you installed jackd ? it looks like you have a different problem to me

---

### Post by d-signet on 2010-04-07
ok, apparently jackd has changed and REALTIME is now the default behavior unless specified.
you can get around it by launching jack control, clicking setup, then changing the server path 

from : 
/usr/bin/jackd

to

/usr/bin/jackd -r

adding the -r tells it to NOT use realtime mode.

this WILL get it 'working', but will give you loads of XRUNs - not working CORRECTLY, but working enough to at least launch programs etc

i'm still (personally) treating this as a bug / mismatched configuration.

---

### Post by billyShears on 2010-04-07
quite strange, I didn't get that error message anymore on 32 bit lucid after adding those two lines to limits.conf.

If you didn't enable realtime process priority when you installed jackd maybe you should try this command in a terminal:
sudo dpkg-reconfigure -p high jackd
and choose "Yes".

You'll need also to add your user to the "audio" group:
sudo usermod -a -G audio yourusernamehere

---

### Post by d-signet on 2010-04-08
is that dependant on having the realtime kernel though? 
My problem was that i had the standard kernel etc installed and couldnt get it to work in NON realtime mode....i know that for best performance etc i should go all out and get the realtime stuff working but I just wanted it working normally to quickly get a mixing job done in ardour
thanks for the suggestions - i'll give them a go tonight

---

### Post by mrowth on 2010-04-08
> **d-signet said:**
> ok, apparently jackd has changed and REALTIME is now the default behavior unless specified.
you can get around it by launching jack control, clicking setup, then changing the server path 

from : 
/usr/bin/jackd

to

/usr/bin/jackd -r

adding the -r tells it to NOT use realtime mode.

Same here; sounds like a bug alright if it doesn't work by just unchecking the "Realtime" option right underneath the "Server Path" field. However, RT mode seems to work (and always has) on the generic kernel. Though IIRC it tends to be crashy when doing any real work.

> this WILL get it 'working', but will give you loads of XRUNs -

Have you increased the "Frames/Period"? To prevent xruns the value needs to be higher when you're not running in realtime mode.

---

### Post by billyShears on 2010-04-08
> **d-signet said:**
> is that dependant on having the realtime kernel though? 
My problem was that i had the standard kernel etc installed and couldnt get it to work in NON realtime mode....i know that for best performance etc i should go all out and get the realtime stuff working but I just wanted it working normally to quickly get a mixing job done in ardour
thanks for the suggestions - i'll give them a go tonight

I'm running jack in realtime mode with a standard 32 bit kernel

---


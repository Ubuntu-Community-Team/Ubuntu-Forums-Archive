---
title: "TOR can't get it to work! help please."
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by trevorxb on 2008-04-06
First off sorry if this is in the wrong category... didn't know where to put it in 3rd party... anyways...

ok so i went to synaptic and checked bastille, privoxy and tor and intalled them... no errors 
(i have NOT run bastille yet)
I then added the torbutton to firefox

ok so i went to two different ip check websites with tor on and off and no luck both see my real ip

i went online tryed to find a fix

here is where i am now ... ( i have not changed any config files)

-----------------------------------------------------------------------------------------------------------

box@box-laptop:~$ tor
Apr 06 12:32:23.516 [notice] Tor v0.1.2.17. This is experimental software. Do not rely on it for strong anonymity.
Apr 06 12:32:23.519 [notice] Initialized libevent version 1.3b using method epoll. Good.
Apr 06 12:32:23.519 [notice] Opening Socks listener on 127.0.0.1:9050
Apr 06 12:32:23.519 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Apr 06 12:32:23.519 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
Apr 06 12:32:23.519 [err] Reading config failed--see warnings above.
box@box-laptop:~$ sudo /etc/init.d/tor stop
Stopping tor daemon: tor.
box@box-laptop:~$ tor
Apr 06 12:34:03.806 [notice] Tor v0.1.2.17. This is experimental software. Do not rely on it for strong anonymity.
Apr 06 12:34:03.809 [notice] Initialized libevent version 1.3b using method epoll. Good.
Apr 06 12:34:03.809 [notice] Opening Socks listener on 127.0.0.1:9050
Apr 06 12:34:04.242 [notice] I learned some more directory information, but not enough to build a circuit.
Apr 06 12:34:07.486 [notice] I learned some more directory information, but not enough to build a circuit.
Apr 06 12:34:07.673 [notice] I learned some more directory information, but not enough to build a circuit.
Apr 06 12:34:09.850 [notice] I learned some more directory information, but not enough to build a circuit.
Apr 06 12:34:09.913 [notice] I learned some more directory information, but not enough to build a circuit.
Apr 06 12:34:10.875 [notice] I learned some more directory information, but not enough to build a circuit.
Apr 06 12:34:10.946 [notice] We now have enough directory information to build circuits.
Apr 06 12:34:13.127 [notice] Tor has successfully opened a circuit. Looks like client functionality is working.


------------------------------------------------------------------------------------------------------------

btw at the end it did not go back to prompt .... i hit ctrl-z after a few mins and while it was sitting there i tryed to use tor in firefox.


ANY help would be great.... i'm a noob (though i have been useing linux for over a year :\ )
so please be specific and step by step.....

THANKS in advance :)

---

### Post by Partyboi2 on 2008-04-07
Have you install and configured privoxy? I was able to get it up and running by using [these]("http://www.torproject.org/docs/tor-doc-unix.html.en") instructions, except I used the tor and privoxy package that is in the ubuntu repo's (they suggest not to) and followed the privoxy config part of the instructions.  Another thing is if you are behind a firewall you may need to open a port. (See step 4)

[extra bits]("https://wiki.torproject.org/noreply/TheOnionRouter/TorifyHOWTO")

---


---
title: "Mythbuntu 13.10 configuration issue"
date: 2013-10-18
forum: Installation &amp; Upgrades
---

### Post by acsidental on 2013-10-18
Hi

I have a slave and master running mythbuntu 13.10. Ever since I've upgraded one will only record zero byte files. The one that records properly is the last one I tuned the tuners on.

If I delete a card it also deletes the same card on the other system.

Also to succesfully see the cards in setup I need to use sudo mythtv-setup otherwise it error's.

Below is the output from mythweb status showing both systems showing "frontend0", from memory this was frontend1 on the slave before the upgrade.

The cards are Master (hvr1200, novat500 "dual tuner"), slave (tristar2, hvr1400)

Encoder 16 [ DVB : /dev/dvb/adapter1/frontend0 ] is remote on mythbuntu and is not recording.
    Encoder 17 [ DVB : /dev/dvb/adapter1/frontend0 ] is remote on mythbuntu and is not recording.
    Encoder 22 [ DVB : /dev/dvb/adapter1/frontend0 ] is local on  michael-desktop and is recording '3 News' on TV3. This recording is  scheduled to end at 7:05 PM.
    Encoder 23 [ DVB : /dev/dvb/adapter1/frontend0 ] is local on michael-desktop and is not recording.
    Encoder 24 [ DVB : /dev/dvb/adapter2/frontend0 ] is local on michael-desktop and is not recording.
    Encoder 25 [ DVB : /dev/dvb/adapter2/frontend0 ] is local on michael-desktop and is not recording.
    Encoder 26 [ DVB : /dev/dvb/adapter3/frontend0 ] is local on michael-desktop and is not recording.
    Encoder 27 [ DVB : /dev/dvb/adapter3/frontend0 ] is local on michael-desktop and is not recording.
    Encoder 28 [ DVB : /dev/dvb/adapter0/frontend0 ] is remote on mythbuntu and is not recording.
    Encoder 29 [ DVB : /dev/dvb/adapter0/frontend0 ] is remote on mythbuntu and is not recording.

Any help appreciated?

Thanks

---

### Post by acsidental on 2013-10-19
OK so I've deleted all the cards on both.

Added a dead sat card to the Master and re added the cards so the card 0 and 1 on both machines are a satellite and a terrestrial, leaving the 2 extra tuners provided by the Nova T500 on the master as 2 and 3.

Now card 1 on the master will not tune even though I know its a working card. Card 0 of course will not work on the master as it is dead.

All other cards seem to work fine.

---

### Post by acsidental on 2013-11-10
Now I'm wondering if my two dead satellite cards are in fact dead as they were cards 1&2 in the master system? and maybe this issue has been building for awhile.

---


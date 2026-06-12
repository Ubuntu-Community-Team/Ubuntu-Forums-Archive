---
title: "Can tune live TV."
date: 2012-09-10
forum: Installation &amp; Upgrades
---

### Post by robhaynes on 2012-09-10
I'm new to this forum and mythbuntu.  I had an earlier version working, but the latest is not happy.  Whenever I try to tune, it just says please wait for a second, then back to the menu.  Judging by the other posts, this symptom seems to occur for many things wrong.  I looked at the logs, and the frontend log just says something bad happened in the backend.  I've posted below what I think are the relevant lines from the backend log.

I'm trying to connect to an HDHomeRun tuner.  It works fine under windows using Windows Media player.  It also works fine on Ubuntu using the HDHomeRun Config GUI.  I've set the default channel to 2_1, which shouldn't be encrypted and tunes fine with the config GUI.

I posted in another thread where a poster described the exact same problem.  But he resolved his problem by configuring a channel grabber and the thread got marked "solved" and people seemed to stop paying attention to the thread.  But the issue was not resolved for me.  I tried configuring Schedules Direct, but that did nothing for me - the symptoms are the same.

mythbackend.log
....
Sep 10 18:47:35 kids mythbackend[2042]: I TVRecEvent tv_rec.cpp:1029 (HandleStateChange) TVRec(1): Changing from None to WatchingLiveTV
Sep 10 18:47:35 kids mythbackend[2042]: I TVRecEvent tv_rec.cpp:3495 (TuningCheckForHWChange) TVRec(1): HW Tuner: 1->1
Sep 10 18:47:35 kids mythbackend[2042]: E TVRecEvent dtvmultiplex.cpp:325 (ParseTuningParams) DTVMux: ParseTuningParams -- Unknown tuner type = 0x2000
Sep 10 18:47:35 kids mythbackend[2042]: E TVRecEvent dtvchannel.cpp:308 (SetChannelByString) DTVChan(1311519D-0): SetChannelByString(2_1): Failed to initialize multiplex options
Sep 10 18:47:35 kids mythbackend[2042]: E TVRecEvent tv_rec.cpp:3681 (TuningFrequency) TVRec(1): Failed to set channel to 2_1. Reverting to kState_None
Sep 10 18:47:35 kids mythbackend[2042]: I TVRecEvent tv_rec.cpp:1029 (HandleStateChange) TVRec(1): Changing from WatchingLiveTV to None

---


---
title: "after upgrade to 18.04 alert sound does not work as expected"
date: 2019-06-21
forum: Installation &amp; Upgrades
---

### Post by Newbunto on 2019-06-21
I recently upgraded from 16.04 to 18.04.

With a desktop that has speakers connected to the Line Out port, the alert sound comes out as two sounds. The expected sound is the sound that has been selected on the Sound Effects tab in the Sound Settings. That comes out - but so does some other sound which is like a "doof" sound, rather unpleasant, rather annoying. Plugging headphones into the Headphones port does not change this behaviour other than that both sounds then come out of the headphones.

With a laptop the behaviour is more complicated. With speakers (or headphones) plugged into the Headphones port, the above misbehaviour occurs. With no speakers plugged in, hence using the built-in speakers, it works correctly.

On either computer, the Output tab of the Sound Settings correctly recognises whether something is plugged into the Headphones port and the Sound Effects tab makes the *correct* sound when the alert sound is selected.

I think this problem may be obvious in 18.04 because there are programs that didn't make the alert sound at all in 16.04 i.e. more occurrences of the alert sound, so more potential for annoyance.

Because settings etc. can be tinkered with, I tested LiveBoot for a range of versions.

Live 16.04, 16.10, 17.04 - can't really test because the functionality is different e.g. doesn't allow me to set the alert sound at all.

Live 18.04.2 - exhibits the exact same problem i.e. it isn't anything to do with any settings that I had made in 16.04 or have made in 18.04

Live 19.04 - functionality changed again but tentatively might be working

Has anyone else observed this behaviour? Is this a known problem that was fixed in 19.04 (or 18.10)? Any known workarounds in 18.04?

---

### Post by Claus7 on 2019-06-21
Hello,

by alert sound do you mean also the sound you might get from pressing tab in terminal and having no more options left, as a result a specific sound is heard so as to notify you about? Having made an upgrade as the one you mention, I have not noticed "double" alert sound in my system. 

One thing that I can think of is the case of two sound cards, yet I think that this is far fetched... You might have checked yet you could use PulseAudio volume control, and by replicating the issue you might be able to see why you have such a double output...

Regards!

---

### Post by Newbunto on 2019-06-21
> **Claus7 said:**
> 
by alert sound do you mean also the sound you might get from pressing tab in terminal and having no more options left
Regards!

In nautilus, click the search icon and then press Backspace in the empty field. Or Backspace in the shell (xterm) when you haven't typed anything (provided that 'Terminal bell' is enabled in the preferences).

---

### Post by Claus7 on 2019-06-21
Hello,

in all cases under 18.04 and 19.04 I do not get any double sound. I tried to reproduce the cases you mention, yet I do not have the same behavior. The alert sound under 18.04 is:
Default
Bark
Drip 
Glass
Sonar.

Having the default it acts as normal. Terminal bell is ticked under the preferences of gnome terminal. 
Under Volume Control and the tab: output devices, I can see the bar increasing every time the alert sound is heard. Zero latency. Maybe checking there might be a right place to start with.

Regards!

---

### Post by Newbunto on 2019-06-22
> Under Volume Control and the tab: output devices, I can see the bar increasing every time the alert sound is heard.

I think that functionality is 19.04 only.? I am suggesting that it *might* be working in 19.04 so one more needs to test under 18.04.

Where you have 18.04, is that a laptop or a desktop?

In 18.04 the Default seems to be Drip. I get "doof" and Drip simultaneously.

---

### Post by Claus7 on 2019-06-24
Hello,

> **Newbunto said:**
> I think that functionality is 19.04 only.? 
No, its under 18.04.
> **Newbunto said:**
> 
I am suggesting that it *might* be working in 19.04 so one more needs to test under 18.04.
The 'tests' are under 18.04.
> **Newbunto said:**
> 
Where you have 18.04, is that a laptop or a desktop?
desktop
> **Newbunto said:**
> 
In 18.04 the Default seems to be Drip. I get "doof" and Drip simultaneously.
Have you tried to change them and check anew what you are getting? Does this "doof" sound persists if another sound is selected?

Regards!

---

### Post by Newbunto on 2019-06-24
> Have you tried to change them and check anew what you are getting?

Yes

> Does this "doof" sound persist if another sound is selected?

Selecting Glass in Settings / Sound / Sound Effects results in the sound made *at the time of selection* being correct (just Glass) but then when I cause the system to output the alert sound I get "doof" and Glass simultaneously.

---

### Post by Claus7 on 2019-06-25
Hello,

it seems that your proposal is about applications then, whereas in my case applications is not an issue, since under the same situations I do not get your output. So I suppose that the problem lies elsewhere: I would advice you once again to open PulseAudio volume control and check from there anything related to the sound issue you are facing. There might be an option selected which makes that annoying sound you mention. Also, you could type alsamixer on a terminal and "play" with the configurations there. First record your original values and then try to tamper with them. If satisfied with the result then you can keep the new configuration. I cannot think any other solution at the moment... apart from:

1) creating a new user and checking if this problem remains the same (I guess not, if live cd has the same behavior)
2) using virtual box and check the options from there...
3) verify that one sound card is the one used and that it does not conflict with any other
sudo inxi -A will list your audio hardware
4) check log messages when you try to reproduce the sound and check if a message appears there

Just some more ideas,
Regards!

---

### Post by Newbunto on 2019-06-27
> creating a new user and checking if this problem remains the same (I guess not, if live cd has the same behavior)

I'm passing on doing that - for the reason that you give.

> verify that one sound card is the one used and that it does not conflict with any other
[FONT=courier new]sudo inxi -A[/FONT] will list your audio hardware

[FONT=courier new]inxi[/FONT] isn't installed out of the box, which could be a problem when doing a Live Boot.

On the normal boot, I installed [FONT=courier new]inxi[/FONT] and it lists two "cards" - 1. via HDMI and 2. "Intel 6 Series/C200 Series Family High Def. Audio Controller"

By contrast, Settings / Sound / Output lists three output choices: 1. via HDMI, 2. S/PDIF and 3. "Speakers (or Headphones) - Built-in Audio". The last one is the only one I use, and it has been working normally for years, prior to the 18.04 upgrade.

With nothing to lose, I tried HDMI. Apart from not working very well at all (inconsistent audio output - sometimes worked and sometimes didn't work, unexpected delay in getting the sound out, variable volume), it exhibited the same problem: "doof" + Glass.

(I tested HDMI by unplugging the speakers from the headphone socket and plugging the speakers in to the monitor. There would not normally be speakers plugged in to the monitor. The monitor does not have its own built-in speakers.)

I don't have the hardware to test S/PDIF and nothing is plugged in to that socket.

> check log messages when you try to reproduce the sound and check if a message appears there

Nothing evident.

When I tried HDMI it complained in syslog that the display doesn't support "3D Vision stereo", whatever that is, but I don't normally use HDMI for audio out, so that doesn't worry me.

---

### Post by Claus7 on 2019-06-27
Hello,

does the last post here eliminates that double sound?
[https://askubuntu.com/questions/980046/2-different-alert-sounds-playing-at-once-in-ubuntu-17-10](https://askubuntu.com/questions/980046/2-different-alert-sounds-playing-at-once-in-ubuntu-17-10)

edit: I was able to come across this as well:
[https://github.com/ubuntu/communitheme-sounds/issues/6](https://github.com/ubuntu/communitheme-sounds/issues/6)

Regards!

---

### Post by Newbunto on 2019-06-27
> [https://askubuntu.com/questions/9800...n-ubuntu-17-10]("https://askubuntu.com/questions/980046/2-different-alert-sounds-playing-at-once-in-ubuntu-17-10")


Thanks for finding that. I had looked around the internet and not found any matching problem descriptions. That is exactly what I am observing. At least I know it is not just me.

> does the last post here eliminate that double sound?

That depends. In that link there are too many people saying "that didn't work for me but here's what did work".

Fumbling around with random combinations of the things that worked for different people, I was able to change

Glass + unpleasant annoying "doof"

into

unpleasant annoying "doof"

so that's progress of a sort. No double sound, but I find it hard to believe that this is working as intended.

18.04 seems very troublesome. Lots of niggly little things like this, whereas 16.04 was rock solid. I'm thinking I might install 19.04 from scratch on a different computer and see whether that works better and then come back to this.

---

### Post by Newbunto on 2019-07-01
> I'm thinking I might install 19.04 from scratch on a different computer and see whether that works better

I've done that. It works correctly.

I changed three things at once
[LIST]
[*]fresh install v. upgrade
[*]19.04 v. 18.04
[*]different computer
[/LIST]

so I can't say what made the difference. It may take a while but eventually I will be able to answer that question

---

### Post by ulrichmuc on 2019-09-05
I have got a similar problem in Ubuntu mate 18.04:
When I set the alert sound (bark) I hear the bark o.k., but
- the volume cannot be adjusted
- backspace in a terminal window (at the start of a line) gives a blob-sound, not the selected bark.
It worked in 16.04

---

### Post by Newbunto on 2019-09-11
Are you in a position to upgrade to 19.04 ?

---

### Post by Newbunto on 2019-09-20
Maybe exercise caution with upgrading to 19.04.

On the *original* computer that had the problem with 18.04, I have got around to upgrading it to 19.04.

That changed things from bad to worse. On 19.04 Sound listed only one "Output Device" something called "Dummy Output" and there was no sound at all when using the "Test" button.

On the other hand, sound devices do still get recognised e.g. **[FONT=courier new][SIZE=3]aplay -l[/SIZE][/FONT]** gives 6 devices (Intel PCH ALC892 Analog, and Digital, plus 4 relating to output via HDMI).

Looking around on the internet, it seems as if other people have had the "Dummy Output" problem before but nothing that I could find worked to get rid of the problem. Testing LiveBoot 19.04 showed that it did work on the old computer. So I blew away the install, installed 19.04 from scratch, and sound now works on the old computer too. Install from scratch was OK for me because I wasn't using that computer any more anyway.

---


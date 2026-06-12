---
title: "Text to speech voices for Ubuntu 12.04"
date: 2021-06-19
forum: Installation &amp; Upgrades
---

### Post by thebishoppear on 2021-06-19
Hello, I am trying to get text to speech voices for Ubuntu 12.04. Specifically, I am trying to get it to announce chess moves. One link which works with Firefox installs espeak with the following command:

**"sudo pacman -S speech-dispatcher espeak"**[COLOR=#BABABA][FONT=&quot]
[/FONT][/COLOR]
However, this only works in Firefox, not Chromium (and I haven't tested Opera yet). The voice is very hard to understand and I would like to get more natural sounding voices. One site has what appears to be what I am looking for but maybe it has been discontinued as I can't get it to work. It is Gespeaker. Does anyone know about this? [http://www.muflone.com/gespeaker/english/download#tabs ]("http://www.muflone.com/gespeaker/english/download#tabs")

If I am correct about it not being supported, then does someone know of another way I can get this to work?

---

### Post by MAFoElffen on 2021-06-19
A few things wrong...

First- Ubuntu 12.04 LTS has not been supported since April 30th, 2017. For anything to work, you would have more luck, with a current version of the OS, which is supported.  That would have a chance at more support for customization (changing voice files). But even so, there is a problem with what else you said.

Second- sSpeak, or Text to Speech does exactly that, it converts text input into an audio format, to add a voice to that text input... Which a "game" playing chess, for eSpeak to work with, would have to be in a text mode (with text on the screen for it to read), which most all recent games are in graphics modes. If a game, where to do that, you would think that it would do that programmatically, not via downgrading it's own experience in graphics. Make sense? So to announce a chess move... well... you see the problem right?

Having said that, in Ubuntu 20.04 LTS, there has been years of improvements in Accessibility Technologies since 12.04. In 20.04, it is under System > Preferences > Assistive  Technologies, and is called the Screen Reader. But even that doesn't work with a lot of programs, which one is Firefox. So for it to work with Screen Reader, there still has to be some collaboration for it to work.

Does that make sense? So I'm not really sure of how to help you if for some reason you have a need to stay on 12.04 or what your underlying goal is...

---

### Post by oldfred on 2021-06-19
thread Closed.

Obsoleted, now unsupported version of Ubuntu.

---


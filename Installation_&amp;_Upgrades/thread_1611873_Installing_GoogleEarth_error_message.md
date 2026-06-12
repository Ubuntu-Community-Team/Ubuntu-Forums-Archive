---
title: "Installing GoogleEarth: error message"
date: 2010-11-02
forum: Installation &amp; Upgrades
---

### Post by aleeming on 2010-11-02
I use a x64 HP laptop, and have Ubuntu 10.10 installed. I wish to install GoogleEarthLinux.bin which I downloaded, then did the usual chmod +x, and ./GoogleEarthLinux.bin, but installation stalled with the message:-
"setup.data/setup.xml:1: parser error : Document is empty

^
setup.data/setup.xml:1: parser error : Start tag expected, '<' not found

^
Couldn't load 'setup.data/setup.xml'
"
Has anyone any ideas about what is wrong?

Thursday 04 Nov 2010
I'm sorry, but I've sorted it on my own: I added 'google software' to my /etc/apt/sources.list:-

#cn for Google Software
deb [url]http://dl.google.com/linux/deb[/ stable non-free

I then downloaded the signing key for Google Packages:-

wget https://dl-ssl.google.com/linux/linux_signing_key.pub[/url] /tmp/key.pub.

Finally I imported the public key into APT:-

sudo apt-key add /tmp/key.pub/linux_signing_key.pub

And that did the trick after a 'Restore' of the Software Resorces.

---


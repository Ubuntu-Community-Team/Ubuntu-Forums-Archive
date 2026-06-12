---
title: "Automate yes answer in ./script installation"
date: 2016-02-18
forum: Installation &amp; Upgrades
---

### Post by steveolive1234 on 2016-02-18
Hey, first time poster here!
 I want to write a script that automates the process of installing my university's VPN service. In order to do that I have to install a file by ./install. This works fine if done from the terminal, but it prompts me with two "yes"/"no" questions, which I have to answer manually. My question now is, whether there is an analogous way to automate a yes answer similar to apt-get --assume-yes for installing programs by ./runscript? 
158

So far I tried:
```
./script <<< "y
y
y
"

```

```
printf 'y\nyes\nno\nmaybe\n' | ./script_that_needs_user_input 

```
but both didn't work. Any tips or suggestions?161

---

### Post by steeldriver on 2016-02-18
Whether there's an --assume-yes equivalent would depend on the writers of the script

The old school way would be to use the 'expect' program, spawning the script and sending appropriate responses when it presents the questions

---


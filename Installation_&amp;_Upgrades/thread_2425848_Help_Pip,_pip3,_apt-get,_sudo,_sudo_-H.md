---
title: "Help: Pip, pip3, apt-get, sudo, sudo -H ???"
date: 2019-08-31
forum: Installation &amp; Upgrades
---

### Post by johantonissen on 2019-08-31
Hi there,

I've recently made a ubuntu server on a rockpi 4b. I want to use this server to give my ipad a true vnc and rdp desktop experience. My main goal is to use Spyer, Texmaker and Jupyter.
I'm currently trying to set everything up but i have found some difficulties installing python 3 libraries. I think this is due to the fact that i'm confused how python libraries are installed. There are so many different methods to do these installations (pip, pip3, apt-get) an then there is also the extremely annoying conflict between python and python3 installation candidates. Furthermore whenever i do a pip installation i can do this using the normal code, sudo + the normal code, and sudo +H + the normal code. I do understand the differences here, but I don't understand what the 'royal way' is to do these installations. Futhermore, I've now installed libraries using all six methods (sudo, sudo +H and regular TIMES pip and pip3 = 6) so it feels like the library installations are a mess at this point.
The result is for example that my jupyter installation does not see my nbextensions.

Can anyone of you more experienced linux users please help me clarify what the 'golden standard' is for installing python3 modules? And what does one do to get order in the chaos at this point ? How can i find the different installation folders of python libraries? And how can I let python3 find the locations and use the libraries in those locations ?

I do know this is a rather vague question, a nice article or book would be just fine. The porblem is just, if I google solutions for my problems every writer uses a different method for installing modules, these might solve the problem in the short run, but cause problems in the long run.

Thank uoi in advance.

Johan

---

### Post by mörgæs on 2019-09-01
As a beginner in Python I understand that the system can be overwhelming. Here are the commands I use for setup:

```
python3 --version
sudo apt install geany
sudo apt install build-essential libssl-dev libffi-dev python3-dev 
sudo apt install python3-pip
pip3 install pandas
pip3 install numpy

```

There could be other ways but so far this has worked well for me. 

Please note that pip3 runs without sudo.

---

### Post by oldfred on 2019-09-01
My system said it had pip3 installed, but I had to reinstall it for it to work. I normally do not use it, but believe it is the recommended way to install python.

sudo apt install python3-pip
pip3 --version
pip 9.0.1 from /usr/lib/python3/dist-packages (python 3.6)

---


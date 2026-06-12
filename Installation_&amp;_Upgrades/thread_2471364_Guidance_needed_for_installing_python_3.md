---
title: "Guidance needed for installing python 3"
date: 2022-01-27
forum: Installation &amp; Upgrades
---

### Post by gangliaghost on 2022-01-27
Hello, 

I am attempting to install python3 using miniconda. I also want to install the spyder package. The official miniconda guide says to download an installation file and run that file. [https://docs.conda.io/projects/conda/en/latest/user-guide/install/linux.html](https://docs.conda.io/projects/conda/en/latest/user-guide/install/linux.html)

Previously, I attempted to install a graphics driver via a .run file, and many problems were caused. So I am hesitant to install via files versus using apt-get or other distro library commands, for example. Basically, I want to know if it is safe to follow this guide. Also, should I install on my SSD which I keep my OS on, or would it be better to install on an HDD that has more storage. Thank you.

---

### Post by him610 on 2022-01-27
Which release of *buntu are you using?
python3 comes with recent releases. It should not be necessary to install it.
From the terminal ....
```

python3 -V

```

---

### Post by MAFoElffen on 2022-01-28
Rather, what to do you want to do and what libraries do you think you will focus on?

Yes If you are on a supported version of any flavor of Ubuntu, you have Python 3 installed already. But it all depends on what you want to focus on and what tool sets you want to use.

I do Python 3 Development, I like to use Eclipse PyDev. There's other things I do with Ananconda.

Honestly, I have never hear of Minconda, but it sounds like maybe a subset of Anaconda, trying to latch on to Anaconda's popularity.

---

### Post by gangliaghost on 2022-01-28
Oh, thank you, I was unaware of this. Able to check and I have Python 3.8 :)

---

### Post by gangliaghost on 2022-01-28
> **MAFoElffen said:**
> Rather, what to do you want to do and what libraries do you think you will focus on?

Yes If you are on a supported version of any flavor of Ubuntu, you have Python 3 installed already. But it all depends on what you want to focus on and what tool sets you want to use.

I do Python 3 Development, I like to use Eclipse PyDev. There's other things I do with Ananconda.

Honestly, I have never hear of Minconda, but it sounds like maybe a subset of Anaconda, trying to latch on to Anaconda's popularity.



Hi. I have used R in the past and mostly have a background in science and data analysis. I thought python would be fun to try and make some simple projects on. I want to learn programming, but I don't currently have money for school. So I figured I would just mess around in my free time. 

Miniconda is a lite version of Anaconda that doesn't install anything but bare minimum of libraries. I was thinking of using it for package management, but tbh I'm not really sure what I'm doing. If it's recommended to just use pip, I'll probably stick with that.

---


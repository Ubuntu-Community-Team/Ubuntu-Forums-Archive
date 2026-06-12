---
title: "Screen resolution and xorg.conf help please."
date: 2006-08-09
forum: Installation &amp; Upgrades
---

### Post by VK2XCI on 2006-08-09
This problem originally arose as "tearing" of the display at 1024x768 when I moved the mouse. I resolved it by changing the "default depth" from 24 to 16.
2 Questions.

1.. Can I simply delete the spurious "Display" subsections? eg deth = 1 etc

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. 86c325 [ViRGE]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

Question 2... If I edit the last two subsections to look like this.

```
SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600" "640x480"
	EndSubSection
```

Will I get 16 bit colour at 1024x768 and 24 bit at the lower resolutions?

I know I could "suck and see" but I'd like to know that Im on the right track. I'm trying to understand a little more of the great mystery ;)

---

### Post by kaffelars on 2006-08-09
1. Yes, you can delete the sections you do not need. But I don't really know what the point is.. ;) 

2. I *think* you're right, but I'm not sure..

---

### Post by VK2XCI on 2006-08-09
> **kaffelars said:**
> 1. Yes, you can delete the sections you do not need. But I don't really know what the point is.. ;) 


I'm just that sort of bloke!  How did "Windows" get to be as bloated as it is? :p 

I remember when the OS, apps and data all fitted on a 720K disk and ran on 32M of Ram! CP/M 80. Guess I show my vintage :-$ 

> 2. I think you're right, but I'm not sure..

Me too! but working on the principle of "first do no harm" I guess I'll wait a little.

---

### Post by kaffelars on 2006-08-09
Well..that *was* a little before my time ;)
But keeping it clean is always a good idea :)

---


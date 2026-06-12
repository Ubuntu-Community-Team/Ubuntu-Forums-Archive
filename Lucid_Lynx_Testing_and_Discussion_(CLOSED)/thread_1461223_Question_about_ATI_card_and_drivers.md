---
title: "Question about ATI card and drivers"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ToxicBurn on 2010-04-23
Im thinking about getting a new ATI card and wanted to know what a good card to get 
 
I play games like world of warcraft in Wine and im looking for a better card then my Nvidia 9800GT whats a good upgrade from the 9800GT on an ATI card and will i have any trouble with drivers in 10.4 ?
 
 
thanks for your help.

---

### Post by psyke83 on 2010-04-23
> **ToxicBurn said:**
> Im thinking about getting a new ATI card and wanted to know what a good card to get 
 
I play games like world of warcraft in Wine and im looking for a better card then my Nvidia 9800GT whats a good upgrade from the 9800GT on an ATI card and will i have any trouble with drivers in 10.4 ?
 
 
thanks for your help.

That's already quite a powerful card, are you sure you need something faster? Most new cards aren't so beneficial on Linux (nowadays, commercial games generally don't use OpenGL,  most new cards are engineered against new DirectX specifications and WINE needs to emulate DirectX calls via OpenGL, anyway).

Also, what does this have to do with the development release?

---

### Post by Reiger on 2010-04-23
Well, as always, depends on how much you want to spend. A ATI 5770 is about &#8364;125,- to &#8364;160,- over here, roughly on par with an ATI 4870 &#8364;130,- to &#8364;150,-. The latter is apparently a bit faster than the former, but the former is a lot less power hungry and needs less cooling. That is actually pretty good money for that much oomph.

If you are willing to fork out substantially more than that a 5850 should get you considerably better performance than either whilst being less power hungry than the 4870 as well. But that retails at: &#8364;250,- to &#8364;285,-. The top of the line (single card) 5870 which is yet more powerful than the 5850 does: &#8364;345,- to &#8364;405,-. 

On the software side: 
The 4870 should work well with FOSS drivers if that is of any concern to you (although the latest driver iteration apparently do funky things to the power/fan management for some people); 

But I doubt that the 5xxx cards will have anywhere near the same amount of functionality in the FOSS drivers just yet. (That will take at least a few releases to sort out; by which time both should have a working gallium 3d driver.) Of course, both should still work under the proprietary fglrx driver.

---

### Post by Didius Falco on 2010-04-24
> **psyke83 said:**
> That's already quite a powerful card, are you sure you need something faster? Most new cards aren't so beneficial on Linux (nowadays, commercial games generally don't use OpenGL,  most new cards are engineered against new DirectX specifications and WINE needs to emulate DirectX calls via OpenGL, anyway).

Also, what does this have to do with the development release?

> will i have any trouble with drivers in 10.4 ?


That part. :)

---

### Post by ToxicBurn on 2010-04-24
> **Didius Falco said:**
> That part. :)
 
Thank you Didius Falco .
 
Had no idea i wasnt supp to talk about video cards and drivers that work or do not work in the RC of 10.4 
 
some people i tell ya.

---


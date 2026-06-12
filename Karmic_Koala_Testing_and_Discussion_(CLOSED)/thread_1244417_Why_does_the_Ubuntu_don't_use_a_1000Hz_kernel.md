---
title: "Why does the Ubuntu don't use a 1000Hz kernel?"
date: 2009-08-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by glasen on 2009-08-19
Why i've asked the question :

After recompiling the standard kernel in Ubuntu with a timer frequency of 1000Hz instead of the the normally used 250Hz, my whole system feels much faster, more responsive (Especially GNOME). The most dramatic effect was that FF3.0 runs approximately 20% faster (Sunspider Javascript Benchmark) : 

[http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?%7B%223d-cube%22:%5B316,293,282,239,262%5D,%223d-morph%22:%5B300,272,262,286,296%5D,%223d-raytrace%22:%5B469,256,251,194,249%5D,%22access-binary-trees%22:%5B121,172,133,140,108%5D,%22access-fannkuch%22:%5B377,332,384,382,370%5D,%22access-nbody%22:%5B353,317,282,290,469%5D,%22access-nsieve%22:%5B159,155,144,137,127%5D,%22bitops-3bit-bits-in-byte%22:%5B143,125,220,170,97%5D,%22bitops-bits-in-byte%22:%5B157,158,173,174,177%5D,%22bitops-bitwise-and%22:%5B165,163,179,165,166%5D,%22bitops-nsieve-bits%22:%5B194,193,200,245,190%5D,%22controlflow-recursive%22:%5B107,109,109,166,71%5D,%22crypto-aes%22:%5B158,161,166,142,193%5D,%22crypto-md5%22:%5B131,131,131,147,113%5D,%22crypto-sha1%22:%5B137,137,246,177,133%5D,%22date-format-tofte%22:%5B406,336,320,357,329%5D,%22date-format-xparb%22:%5B270,216,211,216,267%5D,%22math-cordic%22:%5B261,282,304,415,303%5D,%22math-partial-sums%22:%5B273,297,287,278,274%5D,%22math-spectral-norm%22:%5B187,153,191,158,196%5D,%22regexp-dna%22:%5B483,442,481,453,433%5D,%22string-base64%22:%5B219,224,141,191,155%5D,%22string-fasta%22:%5B325,332,296,305,352%5D,%22string-tagcloud%22:%5B280,311,252,252,242%5D,%22string-unpack-code%22:%5B348,344,425,399,404%5D,%22string-validate-input%22:%5B168,205,204,238,226%5D%7D]("http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?%7B%223d-cube%22:%5B316,293,282,239,262%5D,%223d-morph%22:%5B300,272,262,286,296%5D,%223d-raytrace%22:%5B469,256,251,194,249%5D,%22access-binary-trees%22:%5B121,172,133,140,108%5D,%22access-fannkuch%22:%5B377,332,384,382,370%5D,%22access-nbody%22:%5B353,317,282,290,469%5D,%22access-nsieve%22:%5B159,155,144,137,127%5D,%22bitops-3bit-bits-in-byte%22:%5B143,125,220,170,97%5D,%22bitops-bits-in-byte%22:%5B157,158,173,174,177%5D,%22bitops-bitwise-and%22:%5B165,163,179,165,166%5D,%22bitops-nsieve-bits%22:%5B194,193,200,245,190%5D,%22controlflow-recursive%22:%5B107,109,109,166,71%5D,%22crypto-aes%22:%5B158,161,166,142,193%5D,%22crypto-md5%22:%5B131,131,131,147,113%5D,%22crypto-sha1%22:%5B137,137,246,177,133%5D,%22date-format-tofte%22:%5B406,336,320,357,329%5D,%22date-format-xparb%22:%5B270,216,211,216,267%5D,%22math-cordic%22:%5B261,282,304,415,303%5D,%22math-partial-sums%22:%5B273,297,287,278,274%5D,%22math-spectral-norm%22:%5B187,153,191,158,196%5D,%22regexp-dna%22:%5B483,442,481,453,433%5D,%22string-base64%22:%5B219,224,141,191,155%5D,%22string-fasta%22:%5B325,332,296,305,352%5D,%22string-tagcloud%22:%5B280,311,252,252,242%5D,%22string-unpack-code%22:%5B348,344,425,399,404%5D,%22string-validate-input%22:%5B168,205,204,238,226%5D%7D")

Nothing more than the CONFIG_HZ-option in the kernel-config was changed.

So what are the arguments against using a 1000Hz-Kernel? It seems to me that there are more benefits than drawbacks for using a 1000Hz-Kernel.

---

### Post by fr34k_0/\/_4_1345l-l on 2009-08-19
how do ya do that?

---

### Post by AliTabuger7 on 2009-08-19
It could be simply the fact that you compiled your own kernel. Often times there are several optimizations that can be added, especially if you are using a 32 bit kernel.

---

### Post by Regenweald on 2009-08-19
What are the possible downsides though ? would all software run at this state ?

---

### Post by Copernicus1234 on 2009-08-19
Interesting!

So is it still worth compiling your own kernel these days?

---

### Post by vade on 2009-08-19
I would assume that 1000Hz isn't used by default since it eats up a laptop's battery really fast.

A few ubuntu versions ago, there was a realtime kernel in the repos that not only used 1000Hz ticks but also had full pre-emption enabled for audio people and such that couldn't deal with latencies over some milliseconds. Perhaps there's one for Karmic too, can't check now. It was called -rt or -lowlatency or something like that. I figure that with that kernel the cpu usage will be a bit higher than with the standard kernel.

---

### Post by lukeiamyourfather on 2009-08-19
I would be curious to see benchmarks between different user complied kernels with say 100 HZ, 1,000 HZ, and 10,000 HZ to see what performance benefits there are if any at all.

EDIT: Did a search for benchmarks and saw this comparing 100 HZ to 1,000 HZ and the higher kernel HZ setting negatively impacted performance for larger sets of data. So while reducing latency in some cases its slower overall (by as much as -7% in the conclusion).

[http://www.kernel.org/pub/linux/kernel/people/andrea/misc/31-44-100-1000/31-44-100-1000.html](http://www.kernel.org/pub/linux/kernel/people/andrea/misc/31-44-100-1000/31-44-100-1000.html)

---

### Post by glasen on 2009-08-19
> **AliTabuger7 said:**
> It could be simply the fact that you compiled your own kernel. Often times there are several optimizations that can be added, especially if you are using a 32 bit kernel.

I only changed the 1000Hz-option for this benchmark. All other things were untouched. The kernel i used was a normal ubuntu-kernel (2.6.28-generic).

All other arguments that have been posted :

1. Shorter battery runtime : This is only true for a non-tickless-kernel. As all kernels after version 2.6.21 are using the tickless variant, battery runtime isn't shorter as with 250Hz.

2. Slower in micro-benchmarks : The numbers from the benchmark are from kernel version 2.6.5. This kernel-version is about 5 years old. In meantime many things have changed in the kernel (tickless, other scheduler, etc.).

---

### Post by darthmob on 2009-08-19
> **Chauncellor said:**
> I would be careful with the package, though, because Intrepid's linux-rt kernel broke multi-core cpu functionality, and Jaunty's broke... everything. It was a common bug where the whole system would panic within five minutes of boot.I had that as well and I avoid the rt kernels ever since. :)

---

### Post by Amaranth on 2009-08-19
If you argue that tickless means 1000Hz doesn't hurt battery life it would also not help performance at all.

With a tickless kernel the CONFIG_HZ setting affects how fast/frequently your kernel will respond to an event which can still harm battery life if you turn it up.

---

### Post by hanzomon4 on 2009-08-19
I had so many problems with the pre-rolled rt kernels that just started rolling my own again. But now I can't get the nvidia drivers to load. That patch has been the bane of my sonic existence.

---

### Post by mimor on 2009-08-20
Can someone explain or point out to some information on why one would compile the kernel with a higher rate.
Is it helping in performance for regular desktop systems?

---

### Post by Copernicus1234 on 2009-08-20
> **mimor said:**
> Can someone explain or point out to some information on why one would compile the kernel with a higher rate.
Is it helping in performance for regular desktop systems?

I agree, this would be very interesting to know for everybody who doesnt run Ubuntu on a laptop. Is it worth compiling the kernel with this setting or not?

---

### Post by glasen on 2009-08-20
> Is it worth compiling the kernel with this setting or not?

On a normal desktop system it is definitely worth a try. A 1000Hz-kernel system feels much more snappier (especially GNOME). And, as i stated above, Firefox's Javascript-performance is ~20% higher (tested with FF3.0 and Sunspider).

---

### Post by ilna on 2009-08-20
Is manual kernel rebuilding the only way to use 1000HZ?

---

### Post by Copernicus1234 on 2009-08-20
> **glasen said:**
> On a normal desktop system it is definitely worth a try. A 1000Hz-kernel system feels much more snappier (especially GNOME). And, as i stated above, Firefox's Javascript-performance is ~20% higher (tested with FF3.0 and Sunspider).

Well, as I understood it, you compared a pre-packaged kernel from Ubuntu with your compiled kernel? It could be that the speed improvement comes simply from you compiling your own kernel since then its compiled to take advantage of your specific architecture.

Or are you comparing 2 kernels, both compiled by you, where one has this setting to 1000Hz and the other at 250Hz?

Also, as another user posted, sometimes performance can go down as well: [http://www.kernel.org/pub/linux/kernel/people/andrea/misc/31-44-100-1000/31-44-100-1000.html](http://www.kernel.org/pub/linux/kernel/people/andrea/misc/31-44-100-1000/31-44-100-1000.html)

---

### Post by trulan on 2009-08-20
On a slightly different note:  I don't know what Hz it uses, but the RT kernel is alive and well, for those who would benefit from it.

Ubuntu Hardy had a stable RT kernel.  Intrepid was a different story, but development of the RT-preemption patch had pretty much stopped at that point.  Development resumed again around the time Jaunty was released.  Jaunty's RT kernel was originally supposed to be stable but has issues on some machines.  (It works on my desktop but not my laptop.)

Karmic already has two RT kernels in the repository, one based on 2.6.29 and one on 2.6.31.  Both of them work very well on my desktop (but so does Jaunty's real time kernel so that's not saying much).  But all in all it is very exciting, and as was stated before, it is essential for working with digital audio (especially using a firewire device.)  It's quite feasible to do live signal processing, and to get the actual measured round-trip latency of an audio signal below 10ms.

---

### Post by ext73 on 2009-08-20
> **glasen said:**
> Why i've asked the question :

After recompiling the standard kernel in Ubuntu with a timer frequency of 1000Hz instead of the the normally used 250Hz, my whole system feels much faster, more responsive (Especially GNOME). The most dramatic effect was that FF3.0 runs approximately 20% faster (Sunspider Javascript Benchmark) : 

[http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?%7B%223d-cube%22:%5B316,293,282,239,262%5D,%223d-morph%22:%5B300,272,262,286,296%5D,%223d-raytrace%22:%5B469,256,251,194,249%5D,%22access-binary-trees%22:%5B121,172,133,140,108%5D,%22access-fannkuch%22:%5B377,332,384,382,370%5D,%22access-nbody%22:%5B353,317,282,290,469%5D,%22access-nsieve%22:%5B159,155,144,137,127%5D,%22bitops-3bit-bits-in-byte%22:%5B143,125,220,170,97%5D,%22bitops-bits-in-byte%22:%5B157,158,173,174,177%5D,%22bitops-bitwise-and%22:%5B165,163,179,165,166%5D,%22bitops-nsieve-bits%22:%5B194,193,200,245,190%5D,%22controlflow-recursive%22:%5B107,109,109,166,71%5D,%22crypto-aes%22:%5B158,161,166,142,193%5D,%22crypto-md5%22:%5B131,131,131,147,113%5D,%22crypto-sha1%22:%5B137,137,246,177,133%5D,%22date-format-tofte%22:%5B406,336,320,357,329%5D,%22date-format-xparb%22:%5B270,216,211,216,267%5D,%22math-cordic%22:%5B261,282,304,415,303%5D,%22math-partial-sums%22:%5B273,297,287,278,274%5D,%22math-spectral-norm%22:%5B187,153,191,158,196%5D,%22regexp-dna%22:%5B483,442,481,453,433%5D,%22string-base64%22:%5B219,224,141,191,155%5D,%22string-fasta%22:%5B325,332,296,305,352%5D,%22string-tagcloud%22:%5B280,311,252,252,242%5D,%22string-unpack-code%22:%5B348,344,425,399,404%5D,%22string-validate-input%22:%5B168,205,204,238,226%5D%7D]("http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?%7B%223d-cube%22:%5B316,293,282,239,262%5D,%223d-morph%22:%5B300,272,262,286,296%5D,%223d-raytrace%22:%5B469,256,251,194,249%5D,%22access-binary-trees%22:%5B121,172,133,140,108%5D,%22access-fannkuch%22:%5B377,332,384,382,370%5D,%22access-nbody%22:%5B353,317,282,290,469%5D,%22access-nsieve%22:%5B159,155,144,137,127%5D,%22bitops-3bit-bits-in-byte%22:%5B143,125,220,170,97%5D,%22bitops-bits-in-byte%22:%5B157,158,173,174,177%5D,%22bitops-bitwise-and%22:%5B165,163,179,165,166%5D,%22bitops-nsieve-bits%22:%5B194,193,200,245,190%5D,%22controlflow-recursive%22:%5B107,109,109,166,71%5D,%22crypto-aes%22:%5B158,161,166,142,193%5D,%22crypto-md5%22:%5B131,131,131,147,113%5D,%22crypto-sha1%22:%5B137,137,246,177,133%5D,%22date-format-tofte%22:%5B406,336,320,357,329%5D,%22date-format-xparb%22:%5B270,216,211,216,267%5D,%22math-cordic%22:%5B261,282,304,415,303%5D,%22math-partial-sums%22:%5B273,297,287,278,274%5D,%22math-spectral-norm%22:%5B187,153,191,158,196%5D,%22regexp-dna%22:%5B483,442,481,453,433%5D,%22string-base64%22:%5B219,224,141,191,155%5D,%22string-fasta%22:%5B325,332,296,305,352%5D,%22string-tagcloud%22:%5B280,311,252,252,242%5D,%22string-unpack-code%22:%5B348,344,425,399,404%5D,%22string-validate-input%22:%5B168,205,204,238,226%5D%7D")

Nothing more than the CONFIG_HZ-option in the kernel-config was changed.

So what are the arguments against using a 1000Hz-Kernel? It seems to me that there are more benefits than drawbacks for using a 1000Hz-Kernel.

You have right my compilation of 2.6.28.10 is much faster and have better response than the orginal one ! for example on my lenovo s10 (netbook -> atom 1.6 GHz + GMA 950) Compiz-Fusion works much faster !

and in glxgears i have better score - Compiz-Fuison is working on !

**[COLOR="DarkRed"][glxgears on lenovo s10 with kernel 2.6.10 -> 1000Hz, pat, etc. on]("http://www.fotosik.pl/pokaz_obrazek/pelny/75e44ab2f0b819dc.html")[/COLOR]**

---

### Post by glasen on 2009-08-20
> **Copernicus1234 said:**
> Well, as I understood it, you compared a pre-packaged kernel from Ubuntu with your compiled kernel?

Correct.

> It could be that the speed improvement comes simply from you compiling your own kernel since then its compiled to take advantage of your specific architecture.


I only changed the timer frequency. All other things were untouched. That means no architecture specific optimization, no Preempt-Mode, etc.

> Or are you comparing 2 kernels, both compiled by you, where one has this setting to 1000Hz and the other at 250Hz?


I've also run the test with two identical (except the timer frequency) customized homebrew kernels. In this test the 1000Hz kernel was also faster as the 250Hz kernel. If i find time i will make a small comparison with different kernel options under Karmic.

> Also, as another user posted, sometimes performance can go down as well: [http://www.kernel.org/pub/linux/kernel/people/andrea/misc/31-44-100-1000/31-44-100-1000.html](http://www.kernel.org/pub/linux/kernel/people/andrea/misc/31-44-100-1000/31-44-100-1000.html)

These numbers are for kernel version 2.6.5!!

---

### Post by Copernicus1234 on 2009-08-20
> **glasen said:**
> 
I only changed the timer frequency. All other things were untouched. That means no architecture specific optimization, no Preempt-Mode, etc.


I was under the impression that simply compiling your own kernel (even with the same settings as the pre-packaged kernel) would make it faster, simply because the compiler on your machine will use optimizations. But im not sure, perhaps Im wrong?

Isnt that why Gentoo owners love to compile their own stuff all the time? :)

---

### Post by qamelian on 2009-08-20
> **Copernicus1234 said:**
> I was under the impression that simply compiling your own kernel (even with the same settings as the pre-packaged kernel) would make it faster, simply because the compiler on your machine will use optimizations. But im not sure, perhaps Im wrong?

Isnt that why Gentoo owners love to compile their own stuff all the time? :)
In Gentoo, you still have to specify the architecture specific optimizations to take advantage of them. They don't just happen automatically because you've compiled the code yourself.

---


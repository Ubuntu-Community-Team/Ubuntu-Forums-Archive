---
title: "Nikon DSLR Firmaware Update"
date: 2016-01-28
forum: MINT
---

### Post by MarthonGT on 2016-01-28
Today in the morning I got a message from Nikon that there is a new Firmware available for my D5300 but unfortunately Nikon provides only firmware for Windows and MAC.

After a lengthy research and reading different forums I managed to upgrade the DSLR using only linux (Mint) I do believe that the below steps will work for most of the Nikon DSLR's

I am not much of a big Linux magician but I use only Linux on all my devices for a year or so now and I hope that with this I can help similar users than me, by saving a lot of time for them searching the web.

1. If you did not register your Nikon D5300 with Nikon than here is the [link]("http://downloadcenter.nikonimglib.com/en/download/fw/175.html") ...  If you have a different model than be sure to find the page for your exact Nikon model because while the instructions are similar, the firmware files are not.
2. Download the Windows Firmware
3. In Terminal Navigate to the file for me it was 
cd Downloads 
cd Nikon_D5300Firmware
4. Unpack the file with
unrar e F-D5300-V101W.exe  ( unrar e filename)
5. Format your SD card as per Nikon instruction within your DSLR camera
6. Like me you will most probably bump into the situation that you won't be able to copy the extracted .bin file via usb cable to your camera due write protection.
7. Take out the sd card and put it into your PC
8. If your OS automatically mounts the SD card than you are more lucky than me and just copy the .bin file and than follow the instructions as per Nikon site

9. IF you're not so lucky and your OS gives and error message that it is not able to mount your SD card as exfat is not recognized than in terminal type
sudo apt-get install exfat-utils exfat-fuse  (Exfat fuse I am not sure about but I did install it and it worked for me, but if your are a worried about space on your hard drive try installing only exfat-utils)
10. try to mount again your SD card by pulling out and putting back (YEAH, I am not much of a big typer ;)) in terminal it should be I believe mount -t exfat /dev/sdXX /mnt
11. Now it should mount automatically and you should be able to copy the.bin file to it.
12. Follow the install steps as per Nikon site and at the end you should have the new firmware on the camera installed

This was intended for the everyday people who recently moved to ubuntu or its flavours and are don't really comfortable with "hacking around" nor have IT related jobs or certifications. I think for long time linux users this will cause a small laugh but you never know....

---

### Post by rewyllys on 2016-01-28
@MarthonGT,

Thanks very much for taking the trouble to post your useful guide to updating Nikon DSLR firmware.

---


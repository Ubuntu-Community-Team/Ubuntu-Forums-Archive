---
title: "Ubuntu 10.10 + RFIDIOt  + ACR122"
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by proempiet on 2011-02-11
I am trying to got RIFIOt running with an ACR122 I get to the last point in reading the tags then I get the message below.
 
>>>
proempiet@ubuntu:~/RFIDIOt-1.0a$ ./readtag.py -d -r 0
Reader Subtype: 5
connecting to ACS ACR122U 00 00
readtag v0.1e (using RFIDIOt v1.0a)
Reader: PCSC ACS ACR122U 00 00
disconnecting from ACS ACR122U 00 00
connecting to ACS ACR122U 00 00
> FF CA 00 00 00
ID: 
Data:
disconnecting from ACS ACR122U 00 00
connecting to ACS ACR122U 00 00
> FF CA 00 00 00
Block 00: > FF B0 00 00 00
Traceback (most recent call last):
File "./readtag.py", line 41, in <module>
if card.readblock(x):
File "/home/proempiet/RFIDIOt-1.0a/RFIDIOt.py", line 1516, in readblock
ret= self.pcsc_send_apdu(apdu)
File "/home/proempiet/RFIDIOt-1.0a/RFIDIOt.py", line 1321, in pcsc_send_apdu
result, sw1, sw2= self.pcsc_connection.transmit(apduout,protocol= self.pcsc_protocol)
File "/usr/local/lib/python2.6/dist-packages/smartcard/CardConnectionDecorator.py", line 82, in transmit
return self.component.transmit(bytes, protocol)
File "/usr/local/lib/python2.6/dist-packages/smartcard/CardConnection.py", line 140, in transmit
data, sw1, sw2 = self.doTransmit(bytes, protocol)
File "/usr/local/lib/python2.6/dist-packages/smartcard/pcsc/PCSCCardConnection.py", line 175, in doTransmit
raise CardConnectionException('Failed to transmit with protocol ' + dictProtocolHeader[pcscprotocolheader] + '. ' + SCardGetErrorMessage(hresult))
smartcard.Exceptions.CardConnectionException: Failed to transmit with protocol T1. Card protocol mismatch.
Exception AttributeError: AttributeError("'NoneType' object has no attribute 'disconnect'",) in <bound method PCSCCardConnection.__del__ of <smartcard.pcsc.PCSCCardConnection.PCSCCardConnection instance at 0x99c9bac>> ignored
>>>
 
Does anybody know what is wrong?

---

### Post by slashmax on 2011-02-17
You're further than me, I think... But, same reader, similar problem.

$ ./readtag.py -d                                                                         
Failed to load symbol for: SCardCancelTransaction, /usr/local/lib/libpcsclite.so.1: undef\
ined symbol: SCardCancelTransaction!                                                      
Reader Subtype: 7                                                                         
connecting to ACS ACR122U PICC Interface 00 00                                            
>  FF 00 00 00 06 D4 32 05 00 00 00                                                       
Traceback (most recent call last):                                                        
  File "./readtag.py", line 24, in <module>                                               
    import RFIDIOtconfig                                                                  
  File "/home/max/NFC/RFIDIOt-1.0a/RFIDIOtconfig.py", line 158, in <module>               
    card= RFIDIOt.rfidiot(readernum,readertype,line,speed,timeout,debug,noinit)           
  File "/home/max/NFC/RFIDIOt-1.0a/RFIDIOt.py", line 147, in __init__                     
    self.acs_set_retry(to)                                                                
  File "/home/max/NFC/RFIDIOt-1.0a/RFIDIOt.py", line 1174, in acs_set_retry               
    return self.acs_send_apdu(self.PCSC_APDU['ACS_SET_RETRY'])                            
  File "/home/max/NFC/RFIDIOt-1.0a/RFIDIOt.py", line 1041, in acs_send_apdu               
    result, sw1, sw2= self.acs_transmit_apdu(apduout)                                     
  File "/home/max/NFC/RFIDIOt-1.0a/RFIDIOt.py", line 1065, in acs_transmit_apdu           
    result, sw1, sw2= self.pcsc_connection.transmit(apdu,protocol= self.pcsc_protocol)    
  File "/usr/lib/pymodules/python2.6/smartcard/CardConnectionDecorator.py", line 81, in t\
ransmit                                                                                   
    return self.component.transmit( bytes, protocol )                                     
  File "/usr/lib/pymodules/python2.6/smartcard/CardConnection.py", line 131, in transmit  
    data, sw1, sw2 = self.doTransmit( bytes, protocol )                                   
  File "/usr/lib/pymodules/python2.6/smartcard/pcsc/PCSCCardConnection.py", line 168, in \
doTransmit                                                                                
    raise CardConnectionException( 'Failed to transmit with protocol ' + dictProtocolHead\
er[pcscprotocolheader] + '. ' + SCardGetErrorMessage(hresult) )                           
smartcard.Exceptions.CardConnectionException: 'Smartcard Exception: Failed to transmit wi\
th protocol T1. Card protocol mismatch.!'                                                 
disconnecting from ACS ACR122U PICC Interface 00 00

---

### Post by slashmax on 2011-02-17
The svn copy of pyscard fixes the undefined symbol in the beginning.

svn co [https://pyscard.svn.sourceforge.net/svnroot/pyscard](https://pyscard.svn.sourceforge.net/svnroot/pyscard) pyscard

---

### Post by gbruno on 2011-10-27
if not T1 then T0 protocol
I'm new to Python, not sure if user can choose protocol...
if T0 then response is 61xx where xx is length of data
get data with a subsequent 'get data' command
- this is GOOD if you are attempting 'wrapped; FF mode
- I havnt got there yet

still stuck on Python weidness...
if you dont set
                   hcard = None
then Python crashes if you test hcard
.... what is less  than None??
.... what is hcard anyway???

I will attempt to set it to 'TOAST' if not None   <<do NOT do this

hcard is card handle 

 File "/usr/local/lib/python2.7/dist-packages/smartcard/scard/scard.py", line 505, in SCardControl
    return _scard.SCardControl(*args)

TypeError: Expected a python long as SCARDHANDLE.
disconnecting from ACS ACR38U-CCID 01 00

.......................................................

ps: I was doing much better BEFORE i installed the Linux ACS driver - it seems that some default reader driver was better!!

RFIDIOt is stuffed full of low level reader-type flags and fields...
My Advice:  Abandon automatic detection of readers.
First step: decide on your reader and dont go reading obscure EEPROM bytes, they may not be there...

---


---
title: "Serial Port Read Problems"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sprince09 on 2009-10-19
Hi guys,

I've got some C code that reads data from a serial port. Actually, I've got a bunch of code that does that. My problem is that the read_serial_port portion of all of this code worked fine in Jaunty, but doesn't seem to work at all in Karmic. I'm fairly certain that I've set up my serial port properly, as I'm able to write to port successfully (I've verified that the proper data is being sent because my micro-controller that I have hooked up to the serial port says so).

However, any time I try to read data from the port, the read times out and I don't get any data back. I know data is there because I can see the Rx LED on my serial adapter light up. 

As far as I know, I've gone through the normal process of opening the serial port using termios.h. 

Anyway, my open port function looks like:

```
char lx_open_port(void){
    /* Opens a serial port using the settings defined by the lynx.port struct.
     * If successful, lynx.port.fd is set as the file descriptor to the port and
     * LX_ERROR_NONE is returned, otherwise LX_ERROR_PORT is returned.
     */
    
    // close port if it's already opened
    if(lynx.port.fd > 0){
        close(lynx.port.fd);
    }
    
    // open port as non-blocking terminal and ignoring the DCD pin
    lynx.port.fd = open(lynx.port.path, O_RDWR | O_NOCTTY);
    if(lynx.port.fd < 0){
        return LX_ERROR_PORT;
    }
    
    // get old termios struct
    // we're going to save the old termios struct so we can reset the serial
    // port to the state we found it in when we close the program
    tcgetattr(lynx.port.fd, &lynx.port.settings);
    lynx.port.old_settings = lynx.port.settings;
    
    // set the baudrate
    lx_set_baudrate(lynx.port.baudrate);
    
    // set port reciever to block until data arrives. Change the 0 to FNDELAY
    // to return immediatly instead of blocking.
    fcntl(lynx.port.fd, F_SETFL, 0);
    
    //enable reciever and set to local mode
    lynx.port.settings.c_cflag |= (CLOCAL | CREAD);

    //clear and set number of databits
    lynx.port.settings.c_cflag &= ~CSIZE;
    switch(lynx.port.data_bits){
        case 6:
            lynx.port.settings.c_cflag |= CS6;
            break;
        
        case 7:
            lynx.port.settings.c_cflag |= CS7;
            break;
        
        case 8:
            lynx.port.settings.c_cflag |= CS8;
            break;
        
        default:
            return LX_ERROR_PORT;
            break;
    }

    //set parity
    lynx.port.settings.c_cflag &= ~PARENB;
    switch(lynx.port.parity){
        case LX_PARITY_EVEN:
            lynx.port.settings.c_cflag |= PARENB;
            break;
        
        case LX_PARITY_ODD:
            lynx.port.settings.c_cflag |= PARODD;
            break;
        
        case LX_PARITY_NONE:
            lynx.port.settings.c_cflag &= ~PARENB;
            break;
        
        default:
            return LX_ERROR_PORT;
            break;
    }

    //set stop bits
    lynx.port.settings.c_cflag &= ~CSTOPB;
    switch(lynx.port.stop_bits){
        case 1:
            lynx.port.settings.c_cflag &= ~CSTOPB;
            break;
        
        case 2:
            lynx.port.settings.c_cflag |= CSTOPB;
            break;
        
        default:
            return LX_ERROR_PORT;
            break;
    }
    

    //disable hardware flow control
    lynx.port.settings.c_cflag &= ~CRTSCTS;

    //set serial driver to transmit raw data (not formatted) and disable 
    //software flow control
    lynx.port.settings.c_lflag &= ~(ICANON | ECHO | ECHOE | ISIG);
    lynx.port.settings.c_iflag &= ~(IXON | IXOFF | IXANY);

    //set port to transmit raw data (not formatted)
    lynx.port.settings.c_oflag &= ~OPOST;

    //set minimum number of characters port reads
    lynx.port.settings.c_cc[VMIN] = 0;

    //set port to timeout if no data is in recieve buffer
    lynx.port.settings.c_cc[VTIME] = lynx.port.timeout/100 + 1;

    //flush buffer and apply changes to port
    tcsetattr(lynx.port.fd, TCSANOW, &lynx.port.settings);

    return LX_ERROR_NONE;
}

```


And a section of my code which reads from the port:

```

    ....
    ....

    write(lynx.port.fd, tmp, 2);//tell controller to give us a value
    read(lynx.port.fd, &retval, 1);
    if(retval == '.'){
        return 0;
    }else
    if(retval == '+'){
        return 1;
    }else{
        return LX_ERROR_COMM;
    }
    ....
    ....


```


Any ideas?

---


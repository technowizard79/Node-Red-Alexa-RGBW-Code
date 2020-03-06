# HA-Alexa
Function node code for controlling RGBW lights with Node-Red Alexa

"node-red-contrib-amazon-echo": https://flows.nodered.org/node/node-red-contrib-amazon-echo

Inspired greatly by "**3ATIVE VFX Studio**" - Please see his video for directions and support:

https://youtu.be/l1as3tYVy64

I'm by no means a Javascript expert, but this code is what worked for me:

- **RGBW Lighting Function Node Code**
```
if (msg.colormode === "hs")
    msg.payload = {
        "service": "turn_on",
        data: {
            "rgb_color": msg.rgb,
            "brightness": msg.bri
        }
    };
else
    msg.payload = {
        "service": "turn_on",
        data: {
            "color_temp": msg.ct,
            "brightness": msg.bri
        }
    };
if (msg.payload === "off") msg.payload = {
    "service": "turn_off"
};
return msg;

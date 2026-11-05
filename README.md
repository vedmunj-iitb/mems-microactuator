# Linear Electrostatic MEMS Microactuator

Design of a MEMS actuator for high-bandwidth fine positioning of a hard-disk head.

Course project, Introduction to MEMS (EE 701), IIT Bombay, Autumn 2025.
Guide: Prof. Ashwin Seshia.

## What I did

- Designed a linear electrostatic microactuator in the SOIMUMPs process.
- Suspended a 1.05 mg proof mass on folded-beam flexures, driven by differential parallel-plate
  electrodes on both sides.
- Derived the linearised drive force, the electrostatic stiffness, the pull-in voltage and the
  displacement transfer functions.
- Sized it for ±1 µm of travel at 1.2 kHz. The design numbers are in the table below.
- Drew the GDS mask layout.

## Design numbers

| Quantity | Value |
|---|---|
| Process | SOIMUMPs |
| Proof mass | 1.05 mg |
| Flexure stiffness | 59.6 N/m |
| Electrodes | differential parallel plates, 12 fingers a side |
| Electrode gap | 2.2 µm |
| Bias voltage | 45 V |
| Drive voltage | 10 V |
| Travel | ±1 µm |
| Natural frequency (flexures and mass) | 1.2 kHz |
| Quality factor | about 5.7 |

## How it works

The proof mass is the moving part. Folded-beam flexures hold it and act as its spring.
Parallel-plate electrodes sit on both sides of the mass. A voltage across a gap pulls the plates
together, and the pull grows with the square of the voltage.

In the differential drive the electrodes on both sides carry the 45 V bias. The 10 V drive is
added on one side and taken away on the other. At the centre the two bias pulls cancel, and what
is left is a force close to proportional to the drive voltage. This is the linearised drive force.

The bias also pulls harder as the mass moves towards one side. That acts like a negative spring,
the electrostatic stiffness, and it softens the suspension. At a high enough bias the negative
spring is as stiff as the flexures, and the mass snaps onto an electrode. That bias is the
pull-in voltage.

The mass, the flexures and the damping (Q about 5.7) make a second-order system. The
displacement transfer functions give the motion of the mass for a given drive voltage or force.

## A quick check

The flexure stiffness and the proof mass give this natural frequency, f = sqrt(k/m) / 2π:

```
$ python3 -c "from math import sqrt, pi; print(f'{sqrt(59.6 / 1.05e-6) / (2 * pi):.0f} Hz')"
1199 Hz
```

That is the 1.2 kHz in the table.

## Not in this repo

The project report and the GDS layout file are not in this repo.

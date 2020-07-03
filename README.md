# Hybrid Helicopter Model

This is a repository for the helicopter SciML challenge problem. The
problem is centered on automatically discovering physically-realistic
augmentations to a model of a laboratory helicopter to better predict
the movement.

## Goals of the Challenge

The challenge is multi-faceted and there is no single number to determine
whether one has done well. However, the features of a solution which
are beneficial are:

- Predictive: Indicators of fit are given by the predicted pitch and
  yaw angles.
- Conservative: the new model is closely based in kind or structure
  to the original mechanistic model. If a very small changes causes
  a very large benefit, this is seen as advantageous to a change that
  throws out the mechanism entirely but receives good predictions.
- Physical: the new model should be able to mechanistically justify
  the terms that are added. Unphysical terms are deemed not desirable
  even if they add to the predictiveness of the model.
- Extrapolatory: Models trained on a subset of the time that can
  extrapolate to future times are deemed advantageous to models that
  utilize the full data.
- Validatable: Models that generate hypotheses that can be independently
  validated are deemed advantageous to models that are a blackbox
  and can only be validated by the exact time series data that is
  used for training/testing.

## Starter Code

The scripts, stored in `/scripts`, are as follows:

- Helicopter.jl: the initial global optimization performed using the
  basic physical equations.
- neural_attempts.jl: the attempted neural augmentation strategies.
  In `_u` the approach is making K nonlinear in u(t), and `_ux`
  allows for the addition of new state-dependent terms.
- equation_discovery.jl: the sparsification of the discovered neural
  neural network. Results in the determination of new physical equations
  and a plot of the accuracy. `_u` is for a version that only is trained
  to add terms based on u(t), while `_ux` allows state-dependent terms
  to be discovered.

The other folders are:

- data: the original data
- figs: the figures generated by the scripts
- optimization_results: the values generated by the scripts, like
  trained neural network parameters and discovered equations
- papers: the work in progress draft

At the top level there is a Project.toml and Manifest.toml for
reproducibility.
